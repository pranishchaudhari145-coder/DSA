1. Pattern Printing (Numbers & Diamond)
#include <stdio.h>
void rightTriangle() { int n, i, j;
printf("Enter number of rows: "); scanf("%d", &n);
for(i=1; i<=n; i++) {

printf("\n");
}
}
void diamondShape() {
int n, i, j, space;
printf("Enter number of rows: "); scanf("%d", &n);
space = n - 1;
for(i=1; i<=n; i++) {
for(j=1; j<=space; j++)
printf(" ");
space--;
for(j=1; j<=2*i-1; j++)
printf("%d", j);
printf("\n");
}
space = 1;
for(i=n-1; i>=1; i--) {
for(j=1; j<=space; j++)
printf(" ");
space++;
for(j=1; j<=2*i-1; j++)
printf("%d", j);
printf("\n");
}
}
int main() {
rightTriangle();
diamondShape();
return 0;
}

2. Pyramid with Asterisks and Alphabets
#include <stdio.h>
void starPyramid(int n) {
for(int i=1; i<=n; i++) {
for(int s=i; s<n; s++) printf(" ");
for(int j=1; j<=2*i-1; j++) printf("*");
printf("\n");
}
}
void alphabetPyramid(int n) {
char ch='A';
for(int i=1;i<=n;i++) {
for(int j=1;j<=i;j++)
printf("%c ",ch++);
printf("\n");
}
}
int main() {
starPyramid(5);
alphabetPyramid(5);
return 0;
}

3. Binary Search on Contact Names

#include <stdio.h>
#include <string.h>
int binarySearch(char names[][20], int n, char target[]) {
int low=0, high=n-1, mid;
while(low<=high) {
mid=(low+high)/2;
if(strcmp(names[mid],target)==0) return mid;
else if(strcmp(names[mid],target)<0) low=mid+1; else high=mid-1;
}
return -1;
}
int main() {
char names[5][20]={"Amit","Bhavya","Kiran","Rohit","Sanjay"}; char target[20];
printf("Enter name to search: "); scanf("%s",target);
int r=binarySearch(names,5,target);
if(r!=-1) printf("%s found at index %d\n",target,r);
else printf("%s not found\n",target);
return 0;
}

4. Bubble Sort and Selection Sort
#include <stdio.h>
void bubbleSort(int a[],int n){
for(int i=0;i<n-1;i++)
for(int j=0;j<n-i-1;j++)
if(a[j]>a[j+1]){
int t=a[j];a[j]=a[j+1];a[j+1]=t;
}
}
void selectionSort(int a[],int n){
for(int i=0;i<n-1;i++){
int min=i;
for(int j=i+1;j<n;j++)
if(a[j]<a[min]) min=j;
int t=a[i];a[i]=a[min];a[min]=t;
}
}
int main(){
int a[]={64,25,12,22,11},b[]={64,25,12,22,11},n=5;
bubbleSort(a,n);
selectionSort(b,n);
printf("Bubble Sorted: ");
for(int i=0;i<n;i++) printf("%d ",a[i]); printf("\nSelection Sorted: ");
for(int i=0;i<n;i++) printf("%d ",b[i]);
return 0;
}

5. Student Database using Structures
#include <stdio.h>
#include <string.h>
struct Student{
int roll;
char name[20];
char dept[10];
char subject[10];
int marks;
};
void add(struct Student s[],int *n){
printf("Enter roll,name,dept,subject,marks: ");
scanf("%d %s %s %s %d",&s[*n].roll,s[*n].name,s[*n].dept,s[*n].subject,&s[*n].marks);

(*n)++;
}
void display(struct Student s[],int n){
for(int i=0;i<n;i++)
printf("%d %s %s %s %d\n",s[i].roll,s[i].name,s[i].dept,s[i].subject,s[i].marks);
}
void search(struct Student s[],int n,int roll){
for(int i=0;i<n;i++)
if(s[i].roll==roll){
printf("Found: %s\n",s[i].name);
return; }
printf("Not found\n"); }
int main(){
struct Student s[10];int n=0;
add(s,&n);add(s,&n); display(s,n);
search(s,n,1);
return 0;
}

6. Stack using Array (Push, Pop, Display)
#include <stdio.h>
#define MAX 5
int stack[MAX], top=-1;
void push(int val){
if(top==MAX-1) printf("Stack Overflow\n");
else stack[++top]=val;
}
void pop(){
if(top==-1) printf("Stack Underflow\n");
else printf("Popped %d\n",stack[top--]);
}
void display(){
if(top==-1) printf("Stack Empty\n");
else for(int i=top;i>=0;i--) printf("%d ",stack[i]);
printf("\n");
}
int main(){
push(10);push(20);push(30);
display(); pop();
display(); return 0;
}

7. Decimal to Binary using Stack
#include <stdio.h>
#define MAX 32
int stack[MAX], top=-1;
void push(int val){stack[++top]=val;} int pop(){return stack[top--];}
int main(){
int n;
printf("Enter decimal number: ");
scanf("%d",&n);
while(n>0){
push(n%2);

}
printf("Binary: ");
while(top!=-1) printf("%d",pop());
return 0;
}

8. Singly Linked List Insert Front/Delete End
#include <stdio.h>
#include <stdlib.h>
struct Node{int data;struct Node*next;};
struct Node*head=NULL;
void insertFront(int val){
struct Node*newNode=malloc(sizeof(struct Node));
newNode->data=val;newNode->next=head;head=newNode;
}
void deleteEnd(){
if(head==NULL) return;
struct Node*temp=head,*prev=NULL;
while(temp->next){prev=temp;temp=temp->next;}
if(prev) prev->next=NULL;
else head=NULL;
free(temp);
}
void display(){
struct Node*t=head;
while(t){printf("%d ",t->data);t=t->next;}
printf("\n");
}
int main(){
insertFront(10);insertFront(20);insertFront(30);
display();
deleteEnd(); display();
return 0;
}

9. Singly Linked List Insert End/Delete Front
#include <stdio.h>
#include <stdlib.h>
struct Node{int data;struct Node*next;};
struct Node*head=NULL;
void insertEnd(int val){
struct Node*newNode=malloc(sizeof(struct Node));
newNode->data=val;newNode->next=NULL;
if(head==NULL){head=newNode;return;}
struct Node*t=head;
while(t->next)t=t->next;
t->next=newNode;
}
void deleteFront(){
if(head==NULL)return;
struct Node*t=head;head=head->next;free(t);
}
void display(){
struct Node*t=head;while(t){printf("%d ",t->data);t=t->next;}printf("\n");
}
int main(){
insertEnd(10);insertEnd(20);insertEnd(30);
display();
deleteFront(); display();

return 0;
}

10. Dynamic Stack using Linked List
#include <stdio.h>
#include <stdlib.h>
struct Node{int data;struct Node*next;};
struct Node*top=NULL;
void push(int val){
struct Node*newNode=malloc(sizeof(struct Node));
newNode->data=val;newNode->next=top;top=newNode;
}
void pop(){
if(top==NULL){printf("Stack Empty\n");return;}
struct Node*t=top;printf("Popped %d\n",t->data);top=top->next;free(t); }
void display(){
struct Node*t=top;while(t){printf("%d ",t->data);t=t->next;}printf("\n");
}
int main(){
push(10);push(20);push(30);
display(); pop();
display(); return 0;
}

11. Binary Search Tree (Traversals)
#include <stdio.h>
#include <stdlib.h>
struct Node{int data;struct Node*left,*right;};
struct Node*newNode(int val){
struct Node*n=malloc(sizeof(struct Node)); n->data=val;n->left=n->right=NULL;
return n;
}
struct Node*insert(struct Node*root,int val){ if(root==NULL)return newNode(val);
if(val<root->data)root->left=insert(root->left,val);
else root->right=insert(root->right,val);
return root;
}
void inorder(struct Node*r){if(r){inorder(r->left);printf("%d ",r->data);inorder(r->right);}}
void preorder(struct Node*r){if(r){printf("%d ",r->data);preorder(r->left);preorder(r->right);}}
void postorder(struct Node*r){if(r){postorder(r->left);postorder(r->right);printf("%d ",r->data);}}
int main(){
struct Node*root=NULL;
root=insert(root,50);insert(root,30);insert(root,70);insert(root,20);insert(root,40); printf("Inorder: ");inorder(root);
printf("\nPreorder: ");preorder(root);
printf("\nPostorder: ");postorder(root);
return 0;
}

12. Graph using Adjacency Matrix & BFS
#include <stdio.h>
#define MAX 10
int adj[MAX][MAX], visited[MAX], n;

void bfs(int start){
int q[MAX], front=0, rear=0; visited[start]=1;
q[rear++]=start;
while(front<rear){
int v=q[front++]; printf("%d ",v);
for(int i=0;i<n;i++){
if(adj[v][i]==1 && ! visited[i]){
visited[i]=1; q[rear++]=i;
}
}
}
}
int main(){
printf("Enter number of vertices: "); scanf("%d",&n);
printf("Enter adjacency matrix:\n");
for(int i=0;i<n;i++)
for(int j=0;j<n;j++)
scanf("%d",&adj[i][j]);
bfs(0);
return 0;
}

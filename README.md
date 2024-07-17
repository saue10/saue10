#include<stdio.h>
#include<stdlib.h>
struct node{
    struct node *prev;
    int data;
    struct node *next;
};
int counter();
struct node *head;
void insertAtEnd(int item)
{
    struct node*ptr,*temp;
    temp=(struct node*)malloc(sizeof(struct node));
    
    if(temp!=NULL)
    { 
        temp->prev=NULL;
        temp->data=item;
        temp->next=NULL;
        if(head==NULL)
        {
            head=temp;
            return;
        }
        ptr=head;
        while(ptr->next!=NULL)
        {
            ptr=ptr->next;
        }   
        ptr->next=temp;
        temp->prev=ptr;
    }
}
void insertAtBeg(int item)
{
    struct node*ptr,*temp;
    temp=(struct node*)malloc(sizeof(struct node));
    
    if(temp!=NULL)
    { 
        temp->prev=NULL;
        temp->data=item;
        temp->next=NULL;
        if(head==NULL)
        {
            head=temp;
            return;
        }
        ptr=head;
        temp->next=ptr;
        ptr->prev=temp;
        head=temp;  
    
    }
}
void insertAtLoc(int item,int key)
{
    struct node*ptr,*temp;
    temp=(struct node*)malloc(sizeof(struct node));
    
    if(temp!=NULL)
    { 
        temp->prev=NULL;
        temp->data=item;
        temp->next=NULL;
        if(head==NULL)
        {
            head=temp;
            return;
        }
        ptr=head;
        while(ptr->data!=key)
        {
            ptr=ptr->next;
        } 
        temp->next=ptr->next; 
        ptr->next->prev=temp; 
        ptr->next=temp;
        temp->prev=ptr;
        
    }
}
void deleteAtEnd()
{
    struct node*ptr;

    if(head==NULL)
    {
       return;
    }
    ptr=head;
    while(ptr->next->next!=NULL)
    {
        ptr=ptr->next;
    }   
    free(ptr->next->next);
    ptr->next=NULL;
}
void deleteAtBeg()
{
    struct node*ptr;

    if(head==NULL)
    {
       return;
    }
    ptr=head;
    head=ptr->next;   
    free(ptr);
    head->prev=NULL;
}
void deleteAtLoc(int key)
{
    struct node*ptr,*temp1,*temp2;

    if(head==NULL)
    {
       return;
    }
    ptr=head;
    while(ptr->data!=key)
    {
        ptr=ptr->next;
    } 
    temp1=ptr->prev;
    temp2=ptr->next;
    temp1->next=temp2;
    temp2->prev=temp1;  
    free(ptr);
    
}
int counter()
{
    struct node*ptr;
   
    ptr=head;
     int count=0;
    while(ptr!=NULL)
    {
       count++;
       ptr=ptr->next;
    }
    return count;
}

void display()
{
    struct node* temp;
    temp=head;
    while(temp!=NULL)
    {
        printf("%d ->",temp->data);
        temp=temp->next;
    }
}
int main()
{
   insertAtEnd(10);
   insertAtEnd(20);
   insertAtEnd(30);
   insertAtEnd(40);
   insertAtEnd(50);
   display();
   insertAtBeg(80);
   printf("\n");
   display();
   insertAtLoc(100,30);
   printf("\n");
   display();
   deleteAtEnd();
   printf("\n");
   display();
   deleteAtBeg();
   printf("\n");
   display();
   deleteAtLoc(30);
   printf("\n");
   display();
   printf("\n");
   int x=counter();
   printf("the length of the doubly linked list is: %d",x);
   
}
<!---
saue10/saue10 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

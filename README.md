# single-linked-list
single linked list code with explanation


#include <stdio.h>
#include <stdlib.h>
struct node {
	int data ;
	struct node* link;
	};
struct node* head;
void insert(int x);
int print();
void reverse(){  //reverse the linked list
	struct node *current,*next,*prev;
	current=head;
	prev=NULL;
	while(current!=NULL){
		next=current->link;
		current->link=prev;
		prev=current;
		current=next;
	}
	head=prev;
}
void delete(int n2){        //delete a particular n2 node 
	struct node* temp1=head;
	if(n2==1){
		head=temp1->link;
		free(temp1);
	}
	else{
		for(int i=0;i<n2-2;i++){
			temp1=temp1->link;
		}
		struct node* temp2=temp1->link;
		temp1->link=temp2->link;
		free(temp2);
	}
}	
		
void insert(int x){                                             //insert a value to the linked list 
	struct node*temp=(struct node*)malloc(sizeof(struct node));
	temp->data = x;
	temp->link = head;
	head = temp;
}
void insertAtAfter(int x1,int n1){                                //insert at particular by mentioning their position
	struct node* temp1=head;
	int j=1;                        
	while(j<n1){
		temp1=temp1->link;
		j++;
		}
	struct node* temp2=(struct node*)malloc(sizeof(struct node*));
	temp2->data = x1;
	temp2->link=NULL;
	temp2->link=temp1->link;
	temp1->link=temp2;
}
		
int print(){                      //pritnt the node which is create using insert function
	struct node* temp=head;
	while(temp!=NULL){
		printf("%d ",temp->data);
		temp=temp->link;
	}
}
	
	

int main(){`                      //driver function
	head = NULL;
	
	int x,n,x1,n1,n2;
	printf("enter the size");
	scanf("%d",&n);
	for(int i=0;i<n;i++){
		printf("enter the no ");
		scanf("%d",&x);
		insert(x);
		
		printf("\n");
	}
	printf("enter the value and their pos");
	scanf("%d %d",&x1,&n1);
	insertAtAfter(x1,n1);
	printf("enter the pos to delete");
	scanf("%d",&n2);
	delete(n2);
	reverse();
	print();

	


	return 0;
}


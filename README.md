# dsaassignment.c
/*Name - Rhisav Bora
Scholar id - 2012080
Sec A(CSE)
*/

//1)
#include<stdio.h>

int validfloat(char str[], int b){
    int c=0;
    for(int i=0; i<b; i++){
        if(str[i]=='.'&& str[i+1]!='\0'){
            if(c==0){
                c=1;
            }
            else{
                return 0;
            }
        }
        if(str[i]<46||str[i]>57||str[i]==47){
            return 0;
        }
    }
    if(c==1){
        return 1;
    }
    else{
        return 0;
    }
}
int main(){
    int b;
    printf("Enter the length of the number: \n");
    scanf("%d", &b);
    char str[b+2];
    printf("Enter the number: \n");
    scanf("%s", &str);
    if(validfloat(str, b)==1){
        printf("valid");
    }
    else{
        printf("not valid");
    }
    return 0;
}

//2)

#include <stdio.h>
#define MAX 50
int validDomain(char email[], int atIndex)
{
  int periodIndex = -1;
  if (email[atIndex + 1] != '.')
  {
    for (int i = atIndex + 2; i < MAX - 1; i++)
    {
      if (email[i] == '.')
        periodIndex = i;
    }
    if (periodIndex == -1)
      return 0;
    else
      return 1;
  }
  else
    return 0;
}
int isValidEmail(char email[])
{
  int atIndex = -1;
  for (int i = 0; i < MAX - 4; i++)
  {
    if (email[i] == '@')
      atIndex = i;
  }
  if (atIndex == -1)
    return 0;
  else
    return validDomain(email, atIndex);
}
int main()
{

  char email[MAX] = {0};
  printf("Enter Email > ");
  scanf("%s", email);

  printf("The email is %s\n", ((isValidEmail(email)) ? "valid" : "invalid"));
  return 0;
}

//3)

#include<stdio.h>

int main()
{
    int row, column;
    printf("Enter the order of 2D matrix (row*col)\n");
    scanf("%d %d",&row,&column);
    int arr[row][column];
    printf("Enter the 2D array\n");
    for(int i=0;i<row;i++)
    {
        for(int j=0;j<column;j++)
            scanf("%d",&arr[i][j]);
    }
    int n=row*column;
    int b[n];
    int k=0;
    for(int i=0;i<row;i++)
    {
        for(int j=0;j<column;j++)
        {
            b[k]=arr[i][j];
            k++;
        }
    }
    printf("\n Final 1D array:\n");
    for(int i=0;i<n;i++)
        printf("%d ",b[i]);
}

//4)
#include<stdio.h>
#include<time.h>
#include<stdlib.h>
void bubble_sort(int a[], int n)
{
    int counter=1;
    while(counter<n)
    {
        for(int i=0;i<n-counter;i++)
        {
            if(a[i]>a[i+1])
            {
                int temp=a[i];
                a[i]=a[i+1];
                a[i+1]=temp;
            }
        }
        counter++;
    }
}
void selection_sort(int a[], int n)
{
    for(int i=0;i<n;i++)
    {
        int temp=a[i];
        int minIdx=i;
        for(int j=i+1;j<n;j++)
        {
            if(a[j]<temp){
                minIdx=j;
                temp=a[j];
            }
        }
        temp = a[i];
        a[i]=a[minIdx];
        a[minIdx]=temp;
    }
}

int main()
{
    printf("Enter the total number of elements:\n");
    int b;
    scanf("%d",&b);
    int arrsorted1[b], arrunsorted1[b], arrsorted2[b], arrunsorted2[b];
    for(int i=0;i<b;i++){
        arrsorted1[i]=i*100;
        arrsorted2[i]=i*100;
        arrunsorted1[i]=rand();
        arrunsorted2[i]=rand();
        
    }
    clock_t start,end;
    start=clock();
    selection_sort(arrsorted1,b);
    end=clock();
    printf("Total time elapsed for selection sort: %f\n",(double)(end-start)/CLOCKS_PER_SEC);
    printf("Total time taken by selection sort for unsorted array: %f\n",(double)(end-start)/CLOCKS_PER_SEC);
    start=clock();
    selection_sort(arrunsorted1,b);
    end=clock();
    printf("Total time taken by selection sort for sorted array: %f\n",(double)(end-start)/CLOCKS_PER_SEC);



    clock_t start2,end2;
    start2=clock();
    bubble_sort(arrsorted2,b);
    end2=clock();
     printf("Total time elapsed for bubble sort: %f\n",(double)(end2-start2)/CLOCKS_PER_SEC);
     printf("Total time taken by bubble sort for unsorted array: %f\n",(double)(end2-start2)/CLOCKS_PER_SEC);
    start2=clock();
    bubble_sort(arrunsorted2,b);
    end2=clock();
     printf("Total time taken by bubble sort for sorted array: %f\n",(double)(end2-start2)/CLOCKS_PER_SEC);
     return 0;
}

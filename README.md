// LOGIN_PAGE PROJECT -----> 1/29/2023

#include<iostream>
#include<fstream>
#include<string>
using namespace std;

void login();
void registration();
void forgot();

int main(){

int c;
cout<<"\t\t____________________________________________________________________________________\n\n\n";
cout<<"\t\t                                WELCOME TO LOG-IN PAGE                              \n\n\n";
cout<<"\t\t______________________________________  MENU  ______________________________________\n\n\n";
cout<<"\t\t                                                                                    \n\n\n";
cout<<"\t| press 1 to LOGIN                            |"<<endl;
cout<<"\t| press 2 to REGISTER                         |"<<endl;
cout<<"\t| press 3 if you forgot your PASSWORD         |"<<endl;
cout<<"\t| press 4 to EXIT                             |"<<endl;
cout<<"\n\t\t PLEASE ENTER YOUR CHOICE:  ";
cin>>c;
cout<<endl;

switch(c){

case 1:
    login();
    break;
case 2:
    registration();
    break;
case 3:
    forgot();
    break;
case 4:
    cout<<"\t\t\t THANK YOU! \n\n";
    break;

default:
    system("cls");
    cout<<"\t\t\t PLEASE SELECT FROM THE OPTIONS GIVEN ABOVE \n\n"<<endl;
    main();
}

return 0;
}

void login(){

int count;
string userId,password,id,pass;
system("cls");
cout<<"\t\t\t ====================== PLEASE ENTER THE USERNAME AND PASSWORD ============================= "<<endl;
cout<<"\t\t\t USERNAME: ";
cin>>userId;
cout<<"\t\t\t PASSWORD: ";
cin>>password;

ifstream input("records.txt");

while(input>>id>>pass){

    if(id==userId && pass == password){
        count =1;
        system("cls");
    }
}
input.close();

if(count ==1){
    cout<<userId<<"\n your LOGIN is successfull \n Thanks for logging in ! \n";
    main();
}
else{
    cout<<"\n LOGIN ERROR \n please check you username and password\n";
    main();
}
}

void registration(){

string ruserId, rpassword,rid,rpass;
system("cls");
cout<<"\t\t\t Enter The username: ";
cin>>ruserId;
cout<<"\t\t\t Enter The password: ";
cin>>rpassword;

ofstream f1("records.txt",ios::app );
f1<<ruserId<<' '<<rpassword<<endl;
system("cls");

cout<<"\\nt\t\\t Registration is successfull ! \n";
main();

}

void forgot(){

int option ;
system("cls");
cout<<"\t\t\t you forgot the password? No worries \n";
cout<<" Press 1 to search for your username "<<endl;
cout<<" Press 2 to go back to the main menu "<<endl;
cout<<"\t\t\t Enter your choice: ";
cin>>option;

switch(option){

case 1:
{
     int count =0;
    string suserId,sId,spass;
    cout<<"\n\t\t\t Enter the username which you remember: ";
    cin>>suserId;

    ifstream f2("records.txt");

    while(f2>>sId>>spass){
        if(sId == suserId){
            count =1;
        }
    }
    f2.close();
    if(count ==1){
        cout<<"\n\n Your account is found!";
        cout<<"\n\n Your password is: "<<spass;
        main();
    }
    else{
        cout<<"\n\t sorry! your account is not found ! \n";
        main();

    }
    break;
}

case 2:
{
    main();

}
default:
    cout<<"\t\t\t Wrong choice ! Please Try Again "<<endl;
    forgot();
    }

}

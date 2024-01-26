# DiceDestiny-Quest_For_Fortuna
A game of luck and chance
<br>
Coder-Saksham Pahariya

#include <iostream>
#include <string>
#include <time.h>
#include <fstream>
#include <stdlib.h>
#include <conio.h>

using namespace std;

int pts = 100;
int ex = 0, ox = 0, ea = 0, be = 0, a, b;
int pl = 0, ch = 0, ri = 0, mi = 0;
int c1 = 0, c2 = 0, c3 = 0, c4 = 0, w1 = 0, w2 = 0, w3 = 0, w4 = 0; // defining to take record of contest played and win
int l1 = 0, l2 = 0, l3 = 0, l4 = 0;                                 // defining to take record of lose contest
string lol;
float inp;

int findPts(char h)
{ // here defining a function which will
    if (h == 'A')
    {              // return the points after every round and when
        pts += 60; // needed
        return pts;
    }
    else if (h == 'B')
    {
        pts = pts - 30;
        return pts;
    }
    else if (h == 'C')
    {
        pts += 90;
        return pts;
    }
    else if (h == 'D')
    {
        pts = pts - 45;
        return pts;
    }
    else if (h == 'E')
    {
        pts += 150;
        return pts;
    }
    else if (h == 'F')
    {
        pts = pts - 60;
        return pts;
    }
    else if (h == 'G')
    {
        pts += 500;
        return pts;
    }
    else if (h == 'H')
    {
        pts = pts - 150;
        return pts;
    }
    else
    {
        return pts;
    }
}

void rollDie()
{ // create to roll a pair of die
    srand(time(0));
    cout << "\nPress any key to roll the die\n";
    //cin >> inp;
    getch();
    /*while (inp != 1)
    {
        cout << "\nEnter the  correct number please : ";
        cin >> inp;
    }*/
    cout << "\nYour chances are :\n";
    a = (rand() % 6) + 1;
    b = (rand() % 6) + 1;
    cout << "+---+"
         << "\t"
         << "+---+" << endl;
    cout << "| " << a << " |"
         << "\t"
         << "| " << b << " |" << endl;
    cout << "+---+"
         << "\t"
         << "+---+" << endl;
}

void pts60_30()
{ // created for contest1
    srand(time(0));
    int c = (rand() % 5) + 8;
    if (ri == 0)
    {
        cout << "\nIn this contest :" << endl;
        cout << "Two die will be rolled if sum of nos appears on die greater than or equal to random number \n";
        cout << "You will win and get 60 points and if lose points deducted by 30\n\n";
    }
    cout << "\nThe randomly selected number is :" << c << endl;
    rollDie();
    if ((a + b) >= c)
    {
        w1++;
        cout << "you win ";
        cout << "                                                       rem pts : " << findPts('A');
    }
    else
    {
        l1++;
        cout << "you lose ";
        cout << "                                                       rem pts : " << findPts('B');
    }
    cout << endl
         << endl;
}

void pts90_45() // created for contest2
{
    srand(time(0));
    int c = (rand() % 7) + 6;
    if (pl == 0)
    {
        cout << "\nIn this contest :" << endl;
        cout << "Two die will be rolled if sum of nos appears on die less than random number \n";
        cout << "You will win and get 90 points and if lose points deducted by 45\n\n";
    }
    cout << "\nThe randomly selected number is :" << c << endl;
    rollDie();
    if ((a + b) < c)
    {
        w2++;
        cout << "you win ";
        cout << "                                                       rem pts : " << findPts('C');
    }
    else
    {
        l2++;
        cout << "you lose ";
        cout << "                                                       rem pts : " << findPts('D');
    }
    cout << endl
         << endl;
}

void pts150_60() // created for contest3
{
    srand(time(0));
    int c = (rand() % 6) + 3;
    if (ch == 0)
    {
        cout << "\nIn this contest " << endl;
        cout << "Two die will be rolled and dies landed on same number \n";
        cout << "You will win and get 150 points and if lose points deducted by 60\n\n";
    }
    rollDie();
    if (a == b)
    {
        w3++;
        cout << "you win ";
        cout << "                                                       rem pts : " << findPts('E');
    }
    else
    {
        l3++;
        cout << "you lose ";
        cout << "                                                       rem pts : " << findPts('F');
    }
    cout << endl
         << endl;
}

void pts500_150()
{
    srand(time(0));
    int c = (rand() % 10) + 2;
    if (mi == 0)
    {
        cout << "\nIn this contest " << endl;
        cout << "Two die will be rolled if sum of nos appears on die = random number \n";
        cout << "You will win and get 500 points and if lose points deducted by 150\n\n";
    }
    cout << "\nThe randomly selected number is :" << c << endl;
    rollDie();
    if ((a + b) == c)
    {
        w4++;
        cout << "you win ";
        cout << "                                                       rem pts : " << findPts('G');
    }
    else
    {
        l4++;
        cout << "you lose ";
        cout << "                                                       rem pts : " << findPts('H');
    }

    cout << endl
         << endl;
}

int main()
{
    int flag = 0;
    string name;
    ofstream spr;
    spr.open("MyDatabase.txt", ios::app); // saving player's data in MyDatabase.txt file

    cout << "********************************** DIE_LUCK ******************************\n";
    cout << "Here are some set of instructions for you : \n";
    cout << "1. You are given 100 points and your goal is reach 500 points.\n";
    cout << "2. You have to join contest and increase points. \n";
    cout << "3. The rule of contest will be disclosed only after choosing contest.\n";
    cout << "4. If points became zero or less than that you lose the game.\n";

    cout << "Enter your name : ";
    getline(cin, name);
    spr << "\n\nName : " << name << endl; // storing name in file
    while (true)
    {
        while (findPts('I') < 200) // loop to show contest if points are less 200 pts
        {
            ea++; // used to not show new contest unlocked if not change loop
            cout << "\nThere are 2 contest to join \n";
            cout << "1. 60_30\n";
            cout << "2. 90_45\n";
            cout << "Enter the number to select : ";
            cin >> inp;
            while (inp != 2 && inp != 1)
            {
                cout << "\nEnter the correct number : ";
                cin >> inp;
            }
            if (inp == 1)
            {
                pts60_30();
                c1++;
                ri += 1; // variable used to show contest 1 rules 1 time only
                ex++;    // count total no. of contest
            }
            else
            {
                pts90_45();
                c2++;
                pl += 1; // variable used to show contest 2 rules 1 time only
                ex++;
            }
            // Statement to give option to quit if want
            if (ex == 11 || ex == 21 || ex == 31)
            {
                cout << "\nYou have attempted  " << ex << " rounds , it might me hectic.\n";
                cout << "If you want to quit , quit here just type quit or no to continue.\n";
                cin >> lol;
                while (lol != "quit" && lol != "Quit" && lol != "QUIT" && lol != "NO" && lol != "no" && lol != "No")
                {
                    cout << "\nEnter correctly.\n";
                    cin >> lol;
                }
                if (lol == "quit" || lol == "Quit" || lol == "QUIT")
                {
                    flag = 1; // used to escape main while loop
                    break;
                }
            }
            if (findPts('I') <= 0)
            { // Print if lost the game
                flag = 1;
                cout << "\nBad luck , you lost the game , but dont worry .\n";
                cout << "\nGod have some different plans for you.\n";
                break;
            }
        }
        if (flag == 1)
        {
            break;
        }

        while (findPts('I') >= 200 && findPts('I') < 300)
        {
            be++; // not to show instructions if in same level
            if (ea != 0)
            {
                cout << "You have unlocked a new contest my dear.\n";
                cout << "3. 150_60\n";
            }
            ea = 0;
            cout << "\n There are 3 contest to join \n";
            cout << "1. 60_30\n";
            cout << "2. 90_45\n";
            cout << "3. 150_60\n";
            cout << "Enter the number to select : ";
            cin >> inp;
            while (inp != 2 && inp != 1 && inp != 3)
            {
                cout << "\nEnter the correct number : ";
                cin >> inp;
            }
            if (inp == 1)
            {
                pts60_30();
                ri += 1;
                c1++;
                ex++;
            }
            else if (inp == 2)
            {
                pts90_45();
                c2++;
                pl += 1;
                ex++;
            }
            else
            {
                pts150_60();
                ch++; // variable used to show contest 3 rules 1 time only
                c3++;
                ex++;
            }
            if (ex == 11 || ex == 21 || ex == 31)
            {
                cout << "\nYou have attempted  " << ex << " rounds , it might me hectic.\n";
                cout << "If you want to quit , quit here just type quit or no to continue.\n";
                cin >> lol;
                while (lol != "quit" && lol != "Quit" && lol != "QUIT" && lol != "NO" && lol != "no" && lol != "No")
                {
                    cout << "\nEnter correctly.\n";
                    cin >> lol;
                }
                if (lol == "quit" || lol == "Quit" || lol == "QUIT")
                {
                    flag = 1;
                    break;
                }
            }
            if (findPts('I') <= 0)
            {
                flag = 1;
                cout << "\nBad luck , you lost the game , but dont worry .\n";
                cout << "\nGod have some different plans for you\n";
                break;
            }
        }
        if (flag == 1)
        {
            break;
        }

        while (findPts('I') >= 300)
        {
            if (ox == 0 || ox == 3 || ox == 6)
            { // show only 3 times the option to quit
                cout << "Now you have crossed the 300 mark \n";
                cout << "If you want to quit you can quit as well just type 'quit' or 'no' to continue \n";
                cin >> lol;
                while (lol != "quit" && lol != "Quit" && lol != "QUIT" && lol != "NO" && lol != "no" && lol != "No")
                {
                    cout << "\nEnter correctly.\n";
                    cin >> lol;
                }
            }
            ox++;
            if (lol == "quit" || lol == "QUIT" || lol == "Quit")
            {
                cout << endl
                     << name << " you are great but try  some luck out , god bless.";
                flag = 1;
                break;
            }
            else
            {
                if (be != 0)
                {
                    cout << "\nYou have unlocked a new contest my dear.\n";
                    cout << "4. 500_150\n";
                }
                be = 0;
                cout << "\nNow there are only 2 contest to join, and first 2 is cancelled  \n";
                cout << "after crossing 300 points.\n";
                cout << "3. 150_60\n";
                cout << "4. 500_150\n";
                cout << "Enter the number to select : ";
                cin >> inp;
                while (inp != 4 && inp != 3)
                {
                    cout << "\nEnter the correct number : ";
                    cin >> inp;
                }
                if (inp == 3)
                {
                    pts150_60();
                    ch++;
                    c3++;
                    ex++;
                }
                else
                {
                    pts500_150();
                    mi += 1; // variable used to show contest 4 rules 1 time only
                    c4++;
                    ex++;
                }
            }
            if (ex == 11 || ex == 21 || ex == 31)
            {
                cout << "\nYou have attempted  " << ex << " rounds , it might me hectic.\n";
                cout << "If you want to quit , quit here just type quit or no to continue.\n";
                cin >> lol;
                while (lol != "quit" && lol != "Quit" && lol != "QUIT" && lol != "NO" && lol != "no" && lol != "No")
                {
                    cout << "\nEnter correctly.\n";
                    cin >> lol;
                }
                if (lol == "quit" || lol == "Quit" || lol == "QUIT")
                {
                    flag = 1;
                    break;
                }
            }
            if (findPts('I') <= 0)
            {
                flag = 1;
                cout << "\nBad luck , you lost the game , but dont worry .\n";
                cout << "\nGod have some different plans for you\n";
                break;
            }
            if (findPts('I') >= 500)
            {
                cout << "Congratulations " << name << ", you have cleared this game .\n";
                cout << "You are on high luck today , make a wish may god fulfill it\n";
                flag = 1;
                break;
            }
        }
        if (flag == 1)
        {
            break;
        }
    }
    spr.seekp(0);
    // used below syntax to store data in file
    spr << "Contest 1 : 60_30 \nPlayed : " << c1 << "\twin : " << w1 << "\tlose : " << l1 << endl;
    spr << "Contest 2 : 90_45 \nPlayed : " << c2 << "\twin : " << w2 << "\tlose : " << l2 << endl;
    spr << "Contest 3 : 150_60 \nPlayed : " << c3 << "\twin : " << w3 << "\tlose : " << l3 << endl;
    spr << "Contest 4 : 500_150 \nPlayed : " << c4 << "\twin : " << w4 << "\tlose : " << l4 << endl;
    spr.close();
    cout << "\nDo you want to Look on your statistis of win and lose. type 'yes' or 'no'\n";
    cin >> lol;

    if (lol == "YES" || lol == "yes" || lol == "Yes")
    {
        cout << endl;
        cout << "Contest 1 : 60_30 \nPlayed : " << c1 << "\twin : " << w1 << "\tlose : " << l1 << endl;
        cout << "Contest 2 : 90_45 \nPlayed : " << c2 << "\twin : " << w2 << "\tlose : " << l2 << endl;
        cout << "Contest 3 : 150_60 \nPlayed : " << c3 << "\twin : " << w3 << "\tlose : " << l3 << endl;
        cout << "Contest 4 : 500_150 \nPlayed : " << c4 << "\twin : " << w4 << "\tlose : " << l4 << endl;
    }
    return 0;
}
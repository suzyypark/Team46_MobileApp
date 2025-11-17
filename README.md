# Team46_MobileApp

#include <iostream>
#include <vector>
#include <string>
using namespace std;

/* ------------------------------
   Helper: wait for user input
--------------------------------*/
void wait() {
    cout << "\nPress ENTER to continue...";
    cin.ignore();
    cin.get();
}

/* ------------------------------
   QUIZ QUESTIONS
--------------------------------*/
vector<string> questions = {
    "How much do you enjoy reading the news?",
    "How political are your personal interests?",
    "How often do you read science or tech updates?"
};

vector<int> answers;

void startQuiz();
void quizQuestions();
void quizResults();
void home();
void bookTab();
void bookDetails(string title);
void volunteerTab();
void volunteerDetails(string eventName);

/* ------------------------------
   START QUIZ SCREEN
--------------------------------*/
void startQuiz() {
    system("clear || cls");
    cout << "=============================\n";
    cout << "         FEEDFORGE\n";
    cout << "=============================\n\n";
    cout << "1. Start Quiz\n";
    cout << "2. Exit\n\n";
    cout << "Choose: ";

    int choice;
    cin >> choice;

    if (choice == 1) quizQuestions();
    else exit(0);
}

/* ------------------------------
   QUIZ QUESTIONS
--------------------------------*/
void quizQuestions() {
    answers.clear();
    system("clear || cls");

    for (int i = 0; i < questions.size(); i++) {
        cout << "Question " << i + 1 << ": " << questions[i] << "\n\n";
        cout << "Rate 1–5 → ";
        int ans;
        cin >> ans;
        answers.push_back(ans);

        system("clear || cls");
    }

    quizResults();
}

/* ------------------------------
   QUIZ RESULTS
--------------------------------*/
void quizResults() {
    system("clear || cls");

    cout << "============== QUIZ RESULTS ==============\n";
    cout << "Your suggested publications:\n\n";
    cout << "• New York Times\n";
    cout << "• Wall Street Journal\n";
    cout << "• Reuters\n\n";

    cout << "1. Continue to Home\n";
    cout << "2. Retake Quiz\n\n";

    int choice;
    cin >> choice;

    if (choice == 1) home();
    else quizQuestions();
}

/* ------------------------------
   HOME SCREEN
--------------------------------*/
void home() {
    system("clear || cls");

    cout << "================ HOME ================\n";
    cout << "Your personalized FeedForge experience.\n\n";

    cout << "1. Book Recommendations\n";
    cout << "2. Volunteering Events\n";
    cout << "3. Exit\n\n";

    int choice;
    cin >> choice;

    if (choice == 1) bookTab();
    else if (choice == 2) volunteerTab();
    else exit(0);
}

/* ------------------------------
   BOOK TAB
--------------------------------*/
vector<string> books = { "Book One", "Book Two", "Book Three" };

void bookTab() {
    system("clear || cls");

    cout << "========= BOOK RECOMMENDATIONS =========\n\n";
    for (int i = 0; i < books.size(); i++) {
        cout << i + 1 << ". " << books[i] << "\n";
    }
    cout << "\n0. Back\n\n";

    int choice;
    cin >> choice;

    if (choice == 0) home();
    else if (choice >= 1 && choice <= books.size())
        bookDetails(books[choice - 1]);
    else bookTab();
}

/* ------------------------------
   BOOK DETAILS
--------------------------------*/
void bookDetails(string title) {
    system("clear || cls");

    cout << "============== BOOK DETAILS ==============\n";
    cout << "Title: " << title << "\n";
    cout << "Summary: A recommended book for your interests.\n";
    cout << "Price: $9.99\n\n";

    cout << "1. Buy\n";
    cout << "2. Back\n\n";

    int choice;
    cin >> choice;

    if (choice == 2) bookTab();
    else {
        cout << "Thank you for your purchase!\n";
        wait();
        bookTab();
    }
}

/* ------------------------------
   VOLUNTEER TAB
--------------------------------*/
vector<string> events = {
    "Clean the Park",
    "Food Bank Sorting",
    "Animal Shelter Help"
};

void volunteerTab() {
    system("clear || cls");

    cout << "========= VOLUNTEER EVENTS =========\n\n";
    for (int i = 0; i < events.size(); i++) {
        cout << i + 1 << ". " << events[i] << "\n";
    }
    cout << "\n0. Back\n";

    int choice;
    cin >> choice;

    if (choice == 0) home();
    else if (choice >= 1 && choice <= events.size())
        volunteerDetails(events[choice - 1]);
    else volunteerTab();
}

/* ------------------------------
   VOLUNTEER DETAILS
--------------------------------*/
void volunteerDetails(string eventName) {
    system("clear || cls");

    cout << "=========== VOLUNTEER DETAILS ===========\n";
    cout << "Event: " << eventName << "\n";
    cout << "Description: Help your community by participating.\n\n";

    cout << "1. Register\n";
    cout << "2. Back\n\n";

    int choice;
    cin >> choice;

    if (choice == 2) volunteerTab();
    else {
        cout << "You are registered!\n";
        wait();
        volunteerTab();
    }
}

/* ------------------------------
   MAIN
--------------------------------*/
int main() {
    startQuiz();
    return 0;
}

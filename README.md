#  Student Record System (C++ OOP)

```cpp
#include <iostream>
#include <vector>
using namespace std;

class StudentManager {
private:
    struct Student {
        int rollNumber;
        string name;
        vector<int> marks;

        Student(int r, string n, vector<int> m)
            : rollNumber(r), name(n), marks(m) {}
    };

    vector<Student> students;

public:
    void addStudent(int r, string n, vector<int> m) {
        students.emplace_back(r, n, m);
    }

    float calculateAverage(const Student &s) {
        float sum = 0;
        for (int m : s.marks)
            sum += m;
        return s.marks.empty() ? 0 : sum / s.marks.size();
    }

    void displayStudents() {
        for (const auto &s : students) {
            cout << "\nRoll: " << s.rollNumber;
            cout << "\nName: " << s.name;
            cout << "\nMarks: ";
            for (int m : s.marks)
                cout << m << " ";

            cout << "\nAverage: " << calculateAverage(s) << endl;
        }
    }
};

int main() {
    StudentManager sm;

    sm.addStudent(1, "Aman", {80, 85, 90});
    sm.addStudent(2, "Rahul", {70, 75, 78});

    sm.displayStudents();

    return 0;
}

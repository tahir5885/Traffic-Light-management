#include <iostream>
#include <thread>
#include <chrono>
using namespace std;
using namespace std::chrono;
enum Direction { NORTH = 0, EAST, SOUTH, WEST };
string getDirectionName(Direction dir) {
    switch (dir) {
        case NORTH: return "NORTH";
        case EAST: return "EAST";
        case SOUTH: return "SOUTH";
        case WEST: return "WEST";
        default: return "UNKNOWN";
    }
}
void simulateSignal(Direction dir, int greenTime) {

    cout << "\n--------------------------------------\n";
    cout << "RED signal for all directions.\n";
    cout << "GREEN signal for: " << getDirectionName(dir) << "\n";
    this_thread::sleep_for(seconds(greenTime));
    cout << "YELLOW signal for: " << getDirectionName(dir) << "\n";
    this_thread::sleep_for(seconds(2));
}
int main() {
    int cycles;
    cout << "Enter how many times you want to rotate signals: ";
    cin >> cycles;

    int greenTime = 5;

    for (int i = 0; i < cycles; ++i) {
        for (int d = 0; d < 4; ++d) {
            simulateSignal(static_cast<Direction>(d), greenTime);
        }
    }

    cout << "\nSimulation complete.\n";
    return 0;
}

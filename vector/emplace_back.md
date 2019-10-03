#include <iostream>
#include <vector>

class SimpleClass {
private:
    int value;

public:
    explicit SimpleClass(const int& value = 0)
    : value{value} {
        //std::cout << "Constructor" << std::endl;
    }

    /*
    SimpleClass(const SimpleClass& other)
    : value{other.value} {
        std::cout << "Copy constructor" << std::endl;
    }

    SimpleClass(SimpleClass&& other)
    : value(std::move(other.value)) {
        std::cout << "Move constructor" << std::endl;
    }
    */
};

int main() {
    std::vector<SimpleClass> vector;
    vector.reserve(4);

    std::cout << "Emplace back" << std::endl;
    for (int i = 0; i != 2; ++i) {
        vector.emplace_back(5);
    }

    /*
    But we can't use vector.push_back(5) because our SimpleClass has explicit constructer.
    So we used to write next: vector.push_back(SimpleClass(5)).


    std::cout << "Push back" << std::endl;
    for (int i = 0; i != 2; ++i) {
        vector.push_back(SimpleClass(5));
    }
    */

    /*
    Also, we could write: vector.emplace_back(SimpleClass(5)). But in that case our program will
    use extra move constructer. Because emplace_back create SimpleClass element 'inplace'.

    If you remove comment signs in SimpleClass.
    */ 
}

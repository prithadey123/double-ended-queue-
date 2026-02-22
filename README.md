 Overview
This project demonstrates the implementation of a **Deque (Double Ended Queue)** using an array in C.

A Deque allows insertion and deletion from **both ends**:
- Insert at Front
- Insert at Rear
- Delete from Front
- Delete from Rear

This implementation uses a **circular array** to efficiently utilize memory.

--

 Source Code

```c
#include <stdio.h>
#define SIZE 5

int deque[SIZE];
int front = -1;
int rear = -1;

// Check if full
int isFull() {
    return ((rear + 1) % SIZE == front);
}

// Check if empty
int isEmpty() {
    return (front == -1);
}

// Insert at front
void insertFront(int value) {
    if (isFull()) {
        printf("Deque is Full!\n");
        return;
    }

    if (isEmpty()) {
        front = rear = 0;
    } else {
        front = (front - 1 + SIZE) % SIZE;
    }

    deque[front] = value;
    printf("Inserted at front: %d\n", value);
}

// Insert at rear
void insertRear(int value) {
    if (isFull()) {
        printf("Deque is Full!\n");
        return;
    }

    if (isEmpty()) {
        front = rear = 0;
    } else {
        rear = (rear + 1) % SIZE;
    }

    deque[rear] = value;
    printf("Inserted at rear: %d\n", value);
}

// Delete from front
void deleteFront() {
    if (isEmpty()) {
        printf("Deque is Empty!\n");
        return;
    }

    printf("Deleted from front: %d\n", deque[front]);

    if (front == rear) {
        front = rear = -1;
    } else {
        front = (front + 1) % SIZE;
    }
}

// Delete from rear
void deleteRear() {
    if (isEmpty()) {
        printf("Deque is Empty!\n");
        return;
    }

    printf("Deleted from rear: %d\n", deque[rear]);

    if (front == rear) {
        front = rear = -1;
    } else {
        rear = (rear - 1 + SIZE) % SIZE;
    }
}

// Display deque
void display() {
    if (isEmpty()) {
        printf("Deque is Empty!\n");
        return;
    }

    printf("Deque elements: ");
    int i = front;

    while (1) {
        printf("%d ", deque[i]);
        if (i == rear)
            break;
        i = (i + 1) % SIZE;
    }

    printf("\n");
}

// Main function
int main() {
    insertRear(10);
    insertRear(20);
    insertFront(5);
    insertFront(2);

    display();

    deleteFront();
    deleteRear();

    display();

    return 0;
}
```

---

Explanation

 Key Features
- Uses **circular array logic** with modulo operator `%`.
- Allows operations at both ends.
- Prevents overflow and underflow.

 Important Conditions

- **Full Condition:**  
  `(rear + 1) % SIZE == front`

- **Empty Condition:**  
  `front == -1`

 Operations Implemented

- `insertFront()` → Inserts element at the front.
- `insertRear()` → Inserts element at the rear.
- `deleteFront()` → Removes element from the front.
- `deleteRear()` → Removes element from the rear.
- `display()` → Displays all elements from front to rear.

---

 Sample Output

```
Inserted at rear: 10
Inserted at rear: 20
Inserted at front: 5
Inserted at front: 2
Deque elements: 2 5 10 20
Deleted from front: 2
Deleted from rear: 20
Deque elements: 5 10
```

---

 Time Complexity

- Insert Front: **O(1)**
- Insert Rear: **O(1)**
- Delete Front: **O(1)**
- Delete Rear: **O(1)**
- Display: **O(n)**

---

 How to Compile and Run

 Compile:
```
gcc deque.c -o deque
```

 Run:
```
./deque
```

---

 Concepts Used
- Deque Data Structure
- Circular Array
- Modulo Operation
- Overflow & Underflow Handling
- FIFO & LIFO Concepts Combined

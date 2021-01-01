#include<iostream>
#include<conio.h>
using namespace std;
//node structure that can store integers
struct node {
	int data;
	node *next;
	node() {
		data = 0;
		next = NULL;
	}
};

//list class, declare data members as discussed and write constructor
class list {

private:
	int size;
	node *head;
public:
	list() {
		size = 0;
		head = NULL;
	}
	void display();
	bool insert(int);
	void list::insert(node *);
	void removeFirst();
	int search(int);
	int replace(int, int);
	int get(int);
	int getsize();
};
void list::display() {
	node *t = head;
	while (t != NULL) {

		cout << t->data << endl;
		t = t->next;
	}

}
bool list::insert(int a) {
	node *t = new node();
	t->data = a;
	t->next = head;
	head = t;
	size++;
	return true;


}
void list::removeFirst() {
	node *t;
	t = head;
	head = head->next;
	t->next = NULL;
	delete t;
	size--;

}
int list::search(int x) {
	node *t = head;
	int pos = 0;
	while (t != NULL) {
		t = t->next;
		pos++;
		if (t->data == x) {
			return pos;
		}
	}
	return -1;

}
int list::replace(int a, int b) {
	node *t = head;
	int ac = 0;
	while (t != NULL) {
		if (t->data == a) {
			ac++;
			t->data = b;
			t = t->next;
		}


	}
	return ac;

}
void list::insert(node *n) {
	n->next = head;
	head = n;
	size++;

}
int list::get(int a)
{
	node *t;
	t = head;
	for (int i = 0; i < a; i++) {
		t = t->next;

	}
	return t->data;

}

int list::getsize() {
	return size;
}
void main() {

	list l;
	l.insert(21);
	l.insert(54);
	l.insert(67);
	l.insert(88);
	l.insert(44);
	l.insert(33);
	l.insert(48);


	l.display();
	node *n = new node();
	n->data = 189;
	l.insert(n);
	l.display();
	l.removeFirst();
	cout << endl;

	l.display();

	cout << "67 occured " << l.search(67) << " times in the list " << endl;
	cout << endl;
	cout << " 44 is replaced with 99 " << l.replace(44, 99) << " times" << endl;
	cout << endl;


	l.display();
	cout << "At 7th index the number is " << l.get(7) << endl;
	cout << "the size of list is " << l.getsize();


	_getch();
}

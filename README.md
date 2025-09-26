# agl26.09
1)
1. Бинарная куча
· Структура: полное бинарное дерево, хранится в массиве.
· Свойства:
· Min-куча: родитель ≤ потомков.
· Max-куча: родитель ≥ потомков.
· Операции: вставка, извлечение минимума/максимума, удаление.
· Реализация:
· Python: модуль heapq (только min-heap), возможна реализация через класс.
import heapq
```py
# Минимальная куча
heap = []
heapq.heappush(heap, 5)
heapq.heappush(heap, 2)
heapq.heappush(heap, 8)
print(heapq.heappop(heap))  # 2
```
· C++: ручная реализация на основе вектора с методами heapifyUp, heapifyDown.
```cpp
#include <queue>
#include <vector>

// Максимальная куча
std::priority_queue<int> max_heap;
max_heap.push(5);
max_heap.push(2);
max_heap.push(8);
std::cout << max_heap.top(); // 8
max_heap.pop();
```
· Java: класс PriorityQueue, либо ручная реализация через массив.
import java.util.PriorityQueue;
```java
// Минимальная куча
PriorityQueue<Integer> minHeap = new PriorityQueue<>();
minHeap.add(5);
minHeap.add(2);
minHeap.add(8);
System.out.println(minHeap.poll()); // 2
```
2. Биномиальная куча
· Структура: набор биномиальных деревьев разного размера.
· Особенности: поддерживает слияние куч за O(log n).
· Операции: вставка, извлечение минимума, слияние, уменьшение ключа.
· Реализация:
· C++/Java: реализуется через классы с указателями на деревья.
C++
```cpp
#include <boost/heap/binomial_heap.hpp>
boost::heap::binomial_heap<int> bh;
bh.push(5);
bh.push(2);
bh.push(8);
std::cout << bh.top(); // 2
bh.pop();
```
Java
```java
// Используется сторонняя библиотека или реализация
// Пример интерфейса:
BinomialHeap bh = new BinomialHeap();
bh.insert(5);
bh.insert(2);
System.out.println(bh.findMin()); // 2
```
4. Куча Фибоначчи
· Особенности: амортизировано O(1) для вставки и уменьшения ключа, O(log n) для извлечения минимума.
· Применение: алгоритм Дейкстры, приоритетные очереди с частым изменением ключей.
· Реализация:
· C++/Java: возможна реализация через классы с циклическими списками и поддержкой рангов.

C++
```cpp
#include <boost/heap/fibonacci_heap.hpp>
boost::heap::fibonacci_heap<int> fh;
auto handle = fh.push(5);
fh.push(2);
fh.push(8);
fh.decrease(handle, 1); // Уменьшение ключа
std::cout << fh.top(); // 1
```
Java
```java
int[] f = new int[n];
f[0] = 0;
f[1] = 1;
for (int i = 2; i < n; ++i){
    f[i] = f[i - 1] + f[i - 2];
}
```

Python
```py
# Нет в стандартной библиотеке
# Пример интерфейса через стороннюю реализацию:
from fibonacci_heap import FibonacciHeap
fh = FibonacciHeap()
fh.insert(5)
fh.insert(2)
print(fh.extract_min())  # 2
```

2)
Хеш-таблицы
· Структура: массив бакетов, каждый хранит пары «ключ-значение».
· Коллизии разрешаются:
· Метод цепочек (списки в бакетах).
· Открытая адресация (линейное/квадратичное пробирование).
· Операции: вставка, поиск, удаление (в среднем O(1)).
· Реализация:
· Python: встроенный тип dict.
```py
# Встроенный словарь
hash_table = {}
hash_table["key1"] = "value1"
hash_table["key2"] = "value2"
print(hash_table.get("key1"))  # value1
```
· C++: std::unordered_map, либо ручная реализация с цепочками.
```cpp
#include <unordered_map>
std::unordered_map<std::string, int> umap;
umap["apple"] = 10;
umap["banana"] = 20;
std::cout << umap["apple"]; // 10
```
· Java: HashMap, Hashtable (синхронизирован).
```java
import java.util.HashMap;

HashMap<String, Integer> map = new HashMap<>();
map.put("apple", 10);
map.put("banana", 20);
System.out.println(map.get("apple")); // 10
```
Ключевые моменты про кучи

· Бинарные кучи есть во всех языках, эффективны для приоритетных очередей.
· Биномиальные и Фибоначчиевы кучи требуют внешних библиотек или ручной реализации.
· Хеш-таблицы встроены во все языки и используются для быстрого поиска.

Вывод
· Кучи используются для приоритетных очередей.
· Хеш-таблицы — для быстрого поиска и вставки по ключу.
· Выбор структуры зависит от частоты операций и требований к производительности.

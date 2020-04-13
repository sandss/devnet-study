![Python Logo](media/python-logo.png)
## Introduction to Python

#### DevNet Certification Prep

[@ttafsir](https://github.com/ttafsir)


Tafsir Thiam

---

## Outline

* Introduction
* The Python Interpreter
* Basic types: numbers, strings
* container types: list, dictionaries, tuples
* variables
* control structures
* functions

notes:

    We'll discuss the Python interpreter, Python syntax and data types and variables.

---

## Introduction

<div style="text-align: left">

Python is an easy to learn, powerful programming language.

Some key attributes:

* high-level and interpreted language
* object-oriented
* relatively easily to learn
* defacto language for Network Automation

</div>


notes:

    why Python?
    * It's a high-level language, and it includes a lot of built-in functions and a feature rich standard library
    * Large Community == Lots of help
    * Python highly object-oriented language, and we'll look at what that means, but it makes our life easier

---


```python

for device in DEVICES:

    # Connect to device
    ssh = Netmiko(**device)

    # Get command outputs
    lldp_neighbors = ssh.send_command('show lldp neighbor')
    ip_routes = ssh.send_command('show ip route')

    print(lldp_neighbors)
    print(ip_routes)
```

---

# DEMO TIME

---

## The Python Interpreter

* Translates Python code into byte code and evaluates it

* The interpreter is usually installed as <mark>`/usr/local/bin/python`</mark>

* The location of the interpreter is an installation option, so other places are possible

---

## Python 2.x vs Python 3.x

* Python 2.x and Python 3.x are major versions of Python.

* Python 2.x and Python 3.x are not fully compatible (intentionally)

* Support for Python 2.x has been deprecated in January 2020

---

## Python programs

<div style="text-align: left">
Program: sequence of definitions and statements

* Definitions are evaluated
* Statements are executed by the Python Intrepreter
</div>

---

## Python Interpreter

<div style="text-align: left">
Statements are executed in two ways:

* Invoked from the interactive Python Shell
* Executed source code from Python files (*.py)

</div>

notes:

  Interactive shell
  * Great for learning
  * Useful for experimenting

  Python files
  * Useful for making scripts
  * Great for reusability and modularity


---

## Interactive Shell Examples

```python
>>> print("Hello, world")
Hello, world
>>> 2 + 2
4
>>> x = 12**2
>>> x/2
72
>>> # this is a comment
```

---

## Values and Data Types

<div style="text-align: left">

A [**value**]( https://runestone.academy/runestone/books/published/thinkcspy/SimplePythonData/ValuesandDataTypes.html) is one of the fundamental things that a program manipulates. A value in Python is referred to as an **object**.

**objects** fall into different **classes**, or **data types**

> Example: `4` is an _integer_, "Hello World" is a _string_.

```python

# Python can tell you the type of object you're working with!
print(type("hello,world!))
print(type(5))

```

</div>

notes:

    Python programs are meant to manipulate data objects.
    Python objects have a type associated with them, which influences how programs can use them.

---

## Data Types

Built-in data object types:

* int - integer value, `5`
* float - real numbers, ex `5.1`
* bool - boolean values, `True` or `False`
* NoneType - special value, `None`
* str - string of characters

Other useful types: Lists, Dictionaries


notes:

    Built-in data object types:
        int - integer value, 5
        float - real numbers, ex 5.1
        bool - boolean values, True or False
        NoneType - special value, None
        str - string of characters

    we can use type() to see an object's type
    we can convert between types using casting

---

## Numbers

| Type | Examples |
| --- | --- |
|`int` | -1, 0, 134 |
|`float` | -1.0, 0, 5.231 |

---

## Numbers: operations

<small>

| Operation | Result             |
| --------- | ------------------ |
| `x + y`   | sum of *x* and *y* |
| `x - y`   | difference of *x* and *y* |
| `x * y`   | product of *x* and *y*    |
| `x / y`   |   quotient of *x* and *y*  |
| `x // y`  | floored quotient of *x* and *y* |
| `x % y`    | remainder of `x / y`            |
| `int(x)`   | *x* converted to integer        |
| `float(x)` | *x* converted to floating point |
| `x ** y`   | *x* to the power *y*            |

</small>

---

## Strings

```
"Hello, World!"
```

```
'Hello, World!'
```

```
"""
Hello,
World!
"""
```

```
'''
Hello,
World!
'''
```

---

## Strings: operations

<small>

| Operation | Result             | Operation Type |
| --------- | ------------------ | -------------- |
| "hello" + "world"   | 'helloworld' | concactenation |
| "hello" * 3   | 'hellohellohello' | repetition |
| "hello"[0]  | 'h'    | indexing |
| "hello"[-1]  |   'o' | indexing (reversed) |
| "hello"[1:4] | 'ell' | slicing |
| len("hello")    | 5           | size |
| "hello" < "jello"  | True        | comparison |
| "e" in "hello" | True | search |

</small>

---

## Strings: methods

`str` [methods](https://docs.python.org/3/library/stdtypes.html#string-methods) help to transform, test, and search strings

```python

my_string = "my string"

my_string.capitalize()
my_string.lower()
my_string.upper()
my_string.replace()
my_string.split()
my_string.endswith("g")
my_string.islower()
my_string.isupper()
```

The Python [Documentation](https://docs.python.org/3/library/stdtypes.html#string-methods) describes all of the available methods for strings.

---

## Strings: formatting

```python

>>># old
>>>print("Hello, My name is %s" % 'Tafsir')
Hello, My name is Tafsir
>>># new
print("Hello, My name is {}".format('Tafsir'))
Hello, My name is Tafsir
>>># new in Python 3.6+
>>> first_name = "Tafsir"
>>> print(f"{first_name} is my first name")
Tafsir is my first name

```

---

## Type conversion

<small>

| Function | Result |
| -------- | ------ |
| str(x) | x converted to a string |
| int(x) | x converted to integer |
| float(x) | x converted to floating point |

</small>

```sh

>>> str(20)
'20'
>>> int('20')
20
>>> float(20)
20.0
>>>
>>> int('John')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: invalid literal for int() with base 10: 'John'
>>>

```

---

## Variables

* A **variable** is a name that refers to a value.
* Variables DO NOT need to be declared
* Variables DO need to assigned (initialized)
* Variables are not typed

    ```python
    if friendly:
      greeting = "hello world"
    else:
      greeting = 12**2
    print(greeting)
    ```

---

## Variable assignment

```python

>>> year = 2019
>>> print(year)
2019

```

<small> The assignment token, `=`, should not be confused with equality token, `==` </small>

---

## Variable Names

* Must start with a letter or the underscore character.
* Cannot start with a number.
* Can contain only alphanumeric characters and underscores.
* Are case sensitive. (e.g. name and Name are different)

---

## Lists

`list`

* Sequential collection of Python data values, where each value is identified by an index
* The values that make up a list are called its elements
* Lists are similar to strings

```python

string1 = 'Hello'
print(string1[0])

list1 = [0, 'john', '3.1', 3.14 ]
print(list1[1])

```

notes:
    strings are ordered collections of characters, except that the elements of a list can have any type and for any one list, the items can be of different types.

---

## More Lists

In Python, lists can be added to each other using the plus symbol +.

```python

switches = ['sw-ad-3850-1', 'sw-ad-3850-2', 'sw-d-9300-1']
devices = switches + ['rtr-csr-1', 'rtr-asr1k-1']
print(devices)
# ['sw-ad-3850-1', 'sw-ad-3850-2', 'sw-d-9300-1', 'rtr-csr-1', 'rtr-asr1k-1']

```

---

## List Methods

<small>

| Method | Description             |
| --------- | ------------------ |
| append()| Adds an element at the end of the list|
| clear()| Removes all the elements from the list|
| copy()| Returns a copy of the list|
| count()| Returns the number of elements with the specified value|
| extend()| Add the elements of a list (or any iterable), to the end of the current list|
| index()| Returns the index of the first element with the specified value|
| insert()| Adds an element at the specified position|
| pop()| Removes the element at the specified position|
| remove()| Removes the first item with the specified value|
| reverse()| Reverses the order of the list|
| sort()| Sorts the list|

</small>

See the [Documentation](https://docs.python.org/3/tutorial/datastructures.html) for more on list methods.

---

## Dictionaries

`dict`

Dictionaries Python’s built-in mapping type. A map is an unordered, associative collection.

The mapping is from a key (any immutable type) to a value (any Python data object).

```python

device = {
    'hostname': 'router1',
    'vendor': 'Cisco',
    'psu_count': 2
}

```

---

## Dictionaries: Accessing and writing data


```python

device = { 'hostname': 'sw-eos-1', 'vendor': 'Cisco'}
print(device['hostname'])
# sw-eos-1
device['vendor'] = 'Arista'
print(device)
# {'hostname': 'sw-eos-1', 'vendor': 'Arista'}
```

---
## Dictionaries: updating data

Dictionaries can be combined easily with the .update() function

```python
dict1 = {'color': 'blue', 'shape': 'circle'}
dict2 = {'color': 'red', 'number': 42}

dict1.update(dict2)

# dict1 is now {'color': 'red', 'shape': 'circle', 'number': 42}
```

---

## Assignment 1

Add `learn_python3.ipynb` to Jupyter server. 

1. Inside the notebooks directory you used for Jupyter `curl -k -O https://raw.githubusercontent.com/sandss/devnet-study/master/learning-python3.ipynb`
1. In a browser navigate to your Jupyter server.
1. Open `learn_python3.ipynb`

---

## Thank you!

View this presentation online:<br>

 [github.wwt.com/pages/thiamt/python-intro.github.io](https://github.wwt.com/pages/thiamt/python-intro.github.io)

</small>


---

## Useful Links

* [How to Think Like a Computer Scientist: Interactive Edition](https://runestone.academy/runestone/books/published/thinkcspy/index.html)
* [Python Tutor](http://www.pythontutor.com/)
* [python.org](http://www.python.org)

```

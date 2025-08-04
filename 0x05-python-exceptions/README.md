# 0x05. Python - Exceptions

<div align="center">
  <h3>⚠️ Error Handling and Exception Management</h3>
  <p><em>Mastering Python's robust error handling mechanisms</em></p>
</div>

---

## 📋 Description

This project focuses on understanding and implementing exception handling in Python. Students will learn to handle errors gracefully, create custom exceptions, and write robust code that can recover from unexpected situations.

## 🎯 Learning Objectives

By the end of this project, you should be able to explain:

- Why Python programming is awesome
- What's the difference between errors and exceptions
- What are exceptions and how to use them
- When do we need to use exceptions
- How to correctly handle an exception
- What's the purpose of catching exceptions
- How to raise a builtin exception
- When do we need to implement a clean-up action after an exception

## 📚 Resources

- [Errors and Exceptions](https://docs.python.org/3/tutorial/errors.html)
- [Learn to Program 11 Static & Exception Handling](https://www.youtube.com/watch?v=7vbgD-3s-w4)

## 🛠️ Requirements

### Python Scripts
- Allowed editors: `vi`, `vim`, `emacs`
- All files interpreted/compiled on Ubuntu 20.04 LTS using Python3 (version 3.8.5)
- All files should end with a new line
- The first line of all files should be exactly `#!/usr/bin/python3`
- Code should use the pycodestyle (version 2.8.*)
- All files must be executable
- The length of files will be tested using `wc`

## 📁 Files Description

| File | Description |
|------|-------------|
| `0-safe_print_list.py` | Prints x elements of a list safely |
| `1-safe_print_integer.py` | Prints an integer with "{:d}".format() |
| `2-safe_print_list_integers.py` | Prints first x integers of a list |
| `3-safe_print_division.py` | Divides 2 integers and prints result |
| `4-list_division.py` | Divides element by element 2 lists |
| `5-raise_exception.py` | Raises a type exception |
| `6-raise_exception_msg.py` | Raises a name exception with message |
| `100-safe_print_integer_err.py` | Prints integer with error message to stderr |
| `101-safe_function.py` | Executes function safely |
| `102-magic_calculation.py` | Function matching specific bytecode |
| `103-python.c` | C functions that print Python object info |

## 🚀 Usage Examples

### Basic Exception Handling
```python
# 0-safe_print_list.py
def safe_print_list(my_list=[], x=0):
    count = 0
    try:
        for i in range(x):
            print(my_list[i], end="")
            count += 1
    except IndexError:
        pass
    print()
    return count
```

### Try-Except-Finally
```python
# 3-safe_print_division.py
def safe_print_division(a, b):
    result = None
    try:
        result = a / b
    except ZeroDivisionError:
        result = None
    finally:
        print("Inside result: {}".format(result))
    return result
```

### Custom Exceptions
```python
# 5-raise_exception.py
def raise_exception():
    raise TypeError

# 6-raise_exception_msg.py
def raise_exception_msg(message=""):
    raise NameError(message)
```

## 📖 Key Concepts

### Exception Hierarchy
```
BaseException
 +-- SystemExit
 +-- KeyboardInterrupt
 +-- GeneratorExit
 +-- Exception
      +-- StopIteration
      +-- ArithmeticError
      |    +-- ZeroDivisionError
      +-- LookupError
      |    +-- IndexError
      |    +-- KeyError
      +-- ValueError
      +-- TypeError
      +-- NameError
```

### Exception Handling Patterns

#### Basic Try-Except
```python
try:
    risky_operation()
except SpecificException:
    handle_specific_error()
except Exception as e:
    handle_general_error(e)
```

#### Try-Except-Else-Finally
```python
try:
    risky_operation()
except SpecificException:
    handle_error()
else:
    # Runs if no exception occurred
    success_action()
finally:
    # Always runs
    cleanup_action()
```

#### Multiple Exception Types
```python
try:
    risky_operation()
except (ValueError, TypeError) as e:
    handle_multiple_types(e)
except Exception as e:
    handle_other_errors(e)
```

## 🎨 Best Practices

### Exception Handling Guidelines
1. **Be Specific**: Catch specific exceptions, not generic ones
2. **Clean Up**: Use finally blocks for cleanup operations
3. **Don't Ignore**: Never use bare except: clauses
4. **Log Errors**: Record exceptions for debugging
5. **Fail Fast**: Let exceptions bubble up when appropriate

### Error Messages
```python
# Good: Descriptive error messages
raise ValueError("Age must be a positive integer, got: {}".format(age))

# Bad: Generic error messages
raise ValueError("Invalid input")
```

## ⚡ Advanced Topics

### Custom Exception Classes
```python
class CustomError(Exception):
    """Base class for custom exceptions."""
    pass

class ValidationError(CustomError):
    """Raised when input validation fails."""
    def __init__(self, message, code=None):
        super().__init__(message)
        self.code = code
```

### Context Managers for Exception Safety
```python
class ManagedResource:
    def __enter__(self):
        # Acquire resource
        return self
    
    def __exit__(self, exc_type, exc_val, exc_tb):
        # Clean up resource
        if exc_type is not None:
            # Handle exception if needed
            pass
        return False  # Don't suppress exceptions
```

## 🔍 Debugging Tips

1. **Read the Traceback**: Start from the bottom and work up
2. **Use Print Statements**: Add debug prints before risky operations
3. **Check Input Types**: Validate data types before processing
4. **Test Edge Cases**: Consider empty inputs, None values, etc.
5. **Use Debugger**: Step through code with pdb module

## 👨‍💻 Author

**ALX Software Engineering Program**
- Project: 0x05. Python - Exceptions
- Curriculum: Higher Level Programming

---

<div align="center">
  <p><em>Handle errors gracefully, code confidently</em></p>
</div>

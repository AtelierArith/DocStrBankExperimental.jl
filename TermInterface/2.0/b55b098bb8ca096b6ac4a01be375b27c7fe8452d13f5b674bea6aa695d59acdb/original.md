```
arguments(x)
```

Returns the arguments to the function call in a function call expression. `iscall(x)` must be true as a precondition.

Depending on the type and internal representation of `x`, `arguments(x)` may return an unsorted collection nondeterministically, This is to make sure to retrieve the arguments of an expression when the order of arguments does not matter  but the speed of the operation does. To ensure to retrieve arguments in a sorted manner, you can use  and implement the function `sorted_arguments`.

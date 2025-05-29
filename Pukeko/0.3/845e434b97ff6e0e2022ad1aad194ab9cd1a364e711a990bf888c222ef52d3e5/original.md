```
@parametric func iterable
```

Create a version of `func` that is prefixed with `TEST_PREFIX` in the module that this macro is called for each value in `iterable`. If a value in `iterable` is a tuple, it is splatted into the function arguments.

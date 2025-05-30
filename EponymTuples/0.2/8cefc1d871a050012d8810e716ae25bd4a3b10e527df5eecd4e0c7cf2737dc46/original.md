```
@eponymtuple(a, b = bval, ...)
```

Expands to `(a = a, b = bval, ...)`, creating a named tuple.

Each argument is either a symbol, resulting in assigning its own value, or an assignment, passed as is.

The recommended use is the first one, allowing the creation of named tuples without repeating the name. Overriding the value is just for convenience, if you are using it too much you are probably better off with the standard `NamedTuple` constructor `(a = aval, b = bval, ...)`.

```
PyDict{K=Py,V=Py}([x])
```

Wraps the Python dict `x` (or anything satisfying the mapping interface) as an `AbstractDict{K,V}`.

If `x` is not a Python object, it is converted to one using `pydict`.

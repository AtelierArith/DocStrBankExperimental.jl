```
PyList{T=Py}([x])
```

Wraps the Python list `x` (or anything satisfying the sequence interface) as an `AbstractVector{T}`.

If `x` is not a Python object, it is converted to one using `pylist`.

```
PySet{T=Py}([x])
```

Wraps the Python set `x` (or anything satisfying the set interface) as an `AbstractSet{T}`.

If `x` is not a Python object, it is converted to one using `pyset`.

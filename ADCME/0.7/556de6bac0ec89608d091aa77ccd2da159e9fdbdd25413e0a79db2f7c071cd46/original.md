```
spdiag(o::PyObject)
```

Constructs a sparse diagonal matrix where the diagonal entries are `o`, which is equivalent to `spdiag(length(o), 0=>o)`

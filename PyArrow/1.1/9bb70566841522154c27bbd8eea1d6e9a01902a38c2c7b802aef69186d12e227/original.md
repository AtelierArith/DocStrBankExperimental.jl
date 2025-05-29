```
PyArrow.table(src; metadata=nothing, nthreads=nothing) -> Py
```

A wrapper around `pyarrow.table` which converts a Tables.jl-compatible table to a pyarrow table.

Attempts to do so in a zero-copy manner by converting columns to numpy arrays (without copying) before passing to `pa.table`

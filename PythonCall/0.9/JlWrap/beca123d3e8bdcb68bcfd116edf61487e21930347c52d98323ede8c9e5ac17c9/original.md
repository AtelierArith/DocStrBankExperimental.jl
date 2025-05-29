```
pyfunc(f; [name], [qualname], [doc], [signature])
```

Wrap the callable `f` as an ordinary Python function.

The name, qualname, docstring or signature can optionally be set with `name`, `qualname`, `doc` or `signature`.

Unlike `Py(f)` (or `pyjl(f)`), the arguments passed to `f` are always of type `Py`, i.e. they are never converted.

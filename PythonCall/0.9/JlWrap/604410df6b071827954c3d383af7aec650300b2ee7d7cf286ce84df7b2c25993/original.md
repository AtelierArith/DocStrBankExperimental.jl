```
pystaticmethod(f; ...)
```

Convert callable `f` to a Python static method.

If `f` is not a Python object (e.g. if `f` is a `Function`) then it is converted to one with [`pyfunc`](@ref PythonCall.pyfunc). In particular this means the arguments passed to `f` are always of type `Py`. Any keyword arguments are passed to `pyfunc`.

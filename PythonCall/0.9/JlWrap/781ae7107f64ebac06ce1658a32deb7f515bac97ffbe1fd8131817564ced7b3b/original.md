```
pyproperty(; get=nothing, set=nothing, del=nothing, doc=nothing)
pyproperty(get)
```

Create a Python `property` with the given getter, setter and deleter.

If `get`, `set` or `del` is not a Python object (e.g. if it is a `Function`) then it is converted to one with [`pyfunc`](@ref PythonCall.pyfunc). In particular this means the arguments passed to it are always of type `Py`.

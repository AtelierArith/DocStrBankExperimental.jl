```
Py(x)
```

Convert `x` to a Python object, of type `Py`.

Conversion happens according to [these rules](@ref jl2py-conversion).

Such an object supports attribute access (`obj.attr`), indexing (`obj[idx]`), calling (`obj(arg1, arg2)`), iteration (`for x in obj`), arithmetic (`obj + obj2`) and comparison (`obj > obj2`), among other things. These operations convert all their arguments to `Py` and return `Py`.

```
inputvertex(name, size, type::FluxLayer)
```

Return an immutable input type vertex with the given `name` and `size` and a `type` which can be used to  indicate what type of input is expected.

Providing the input type is not strictly necessary for the package to work and in many cases a normal `inputvertex`  will do. 

One example of when it is useful is the [`concat`](@ref) function which needs to know the input type to automatically determine which dimension to concatenate.

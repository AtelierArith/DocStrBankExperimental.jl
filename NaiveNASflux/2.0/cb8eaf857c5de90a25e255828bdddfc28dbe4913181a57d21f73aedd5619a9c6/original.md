```
rnninputvertex(name, size)
```

Return an input type vertex with the given `name` which promises 2D shaped input with `size` number of features suitable for `Flux`s recurrent layers.

Providing the input type is not strictly necessary for the package to work and in many cases a normal `inputvertex`  will do. 

One example of when it is useful is the [`concat`](@ref) function which needs to know the input type to automatically determine which dimension to concatenate.

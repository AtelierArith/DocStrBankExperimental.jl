```
conv1dinputvertex(name, nchannel)
```

Return an input type vertex with the given `name` which promises convolution shaped input  with `nchannel` channels suitable for `Flux`s convolution layers.

Equivalent to [`convinputvertex(name, nchannel, 1)`](@ref). 

Providing the input type is not strictly necessary for the package to work and in many cases a normal `inputvertex`  will do. 

One example of when it is useful is the [`concat`](@ref) function which needs to know the input type to automatically determine which dimension to concatenate.

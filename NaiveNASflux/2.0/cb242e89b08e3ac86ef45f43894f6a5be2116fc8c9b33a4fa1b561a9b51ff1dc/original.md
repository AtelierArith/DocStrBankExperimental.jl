```
convinputvertex(name, nchannel, ndim)
```

Return an input type vertex with the given `name` which promises convolution shaped input  with `nchannel` channels and `ndim` number of dimensions for feature maps (e.g. 2 for images) suitable for `Flux`s convolution layers.

Providing the input type is not strictly necessary for the package to work and in many cases a normal `inputvertex`  will do. 

One example of when it is useful is the [`concat`](@ref) function which needs to know the input type to automatically determine which dimension to concatenate.

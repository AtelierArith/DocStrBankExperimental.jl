```
mutable struct FameObject{CL,FT,FR,DT} … end
```

FAME object of class `CL`, type `FT`, frequency `FR` and data type `DT`.

A `FameObject` is returned by [`quick_info`](@ref) and a vector of `FameObject`s is returned by [`listdb`](@ref). 

Also, a `FameObject` can be constructed directly by calling `FameObject(name, class, type, frequency)` or `FameObject(name, class, type, frequency, first_index, last_index)`. The values of `class`, `type`, and `frequency` can be symbols (like, `:scalar`, `:precision`, etc.) or integers. Refer to the FAME CHLI documentation for the code values.

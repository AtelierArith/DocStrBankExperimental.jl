```
JuliaFunction{DS,S,DT,T}(name::AbstractString, domain::Box{DS,S}, codomain::Box{DT,T})
JuliaFunction(name::AbstractString, domain::Box{DS,S}, codomain::Box{DT,T})
```

Create a zero-valued Julia function, i.e. a Julia function that is zero everywhere. The `codomain` can be a zero-valued domain created via [`Box{DT,T}()`](@ref).

```
coef(r::AbstractDIDResult, name::String)
coef(r::AbstractDIDResult, name::Symbol)
coef(r::AbstractDIDResult, i::Int)
coef(r::AbstractDIDResult, inds)
```

Retrieve a point estimate by name (as in `coefnames`) or integer index. Return a vector of estimates if an iterable collection of names or integers are specified.

Indexing by name requires the method [`coefinds(r)`](@ref). See also [`AbstractDIDResult`](@ref).

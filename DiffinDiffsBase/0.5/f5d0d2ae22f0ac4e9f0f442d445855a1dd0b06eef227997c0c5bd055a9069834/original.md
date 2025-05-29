```
vcov(r::AbstractDIDResult, name1::Union{String, Symbol}, name2::Union{String, Symbol}=name1)
vcov(r::AbstractDIDResult, i::Int, j::Int=i)
vcov(r::AbstractDIDResult, inds)
```

Retrieve the covariance between two coefficients by name (as in `coefnames`) or integer index. Return the variance if only one name or index is specified. Return a variance-covariance matrix for selected coefficients if an iterable collection of names or integers are specified.

Indexing by name requires the method [`coefinds(r)`](@ref). See also [`AbstractDIDResult`](@ref).

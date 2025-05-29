```
getcluster(y::Vector{<:Real}, u::Real; runlength::Int=1)::Vector{Cluster}
```

Extract the clusters from vector `y`.

Threshold exceedances separated by fewer than *r* non-exceedances belong to the same cluster. The value *r* is corresponds to the runlength parameter. This approach is referred to as the *runs declustering scheme* (see Coles, 2001 sec. 5.3.2).

See also [`Cluster`](@ref).

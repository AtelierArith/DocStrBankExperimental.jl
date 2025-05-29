```
broadcasted_normal(mu::AbstractArray{<:Real, N1},
                   std::AbstractArray{<:Real, N2}) where {N1, N2}
```

Samples an `Array{Float64, max(N1, N2)}` of shape `Broadcast.broadcast_shapes(size(mu), size(std))` where each element is independently normally distributed.  This is equivalent to (a reshape of) a multivariate normal with diagonal covariance matrix, but its implementation is more efficient than that of the more general [`mvnormal`](@ref) for this case.

The shapes of `mu` and `std` must be broadcast-compatible.

If all args are 0-dimensional arrays, then sampling via `broadcasted_normal(...)` returns a `Float64` rather than properly returning an `Array{Float64, 0}`.  This is consistent with Julia's own inconsistency on the matter:

```jldoctest
julia> typeof(ones())
Array{Float64,0}

julia> typeof(ones() .* ones())
Float64
```

```
AbstractCovariance{T}
```

Supertype for all covariance functions (singular or not).

## Examples

```jldoctest
julia> Covariance{Float64}<:AbstractCovariance{Float64}
true

julia> SingularCovariance{Int64}<:AbstractCovariance{Int64}
true
```

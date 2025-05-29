```
std_skipmissing(X::AbstractVector{Float64})
std_skipmissing(X::AbstractVector{Union{Missing, Float64}})
```

Compute the standard deviation of the observed values in `X`.

# Examples

```jldoctest
julia> std_skipmissing([1.0; missing; 3.0])
1.4142135623730951
```

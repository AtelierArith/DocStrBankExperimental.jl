```
mean_skipmissing(X::AbstractVector{Float64})
mean_skipmissing(X::AbstractVector{Union{Missing, Float64}})
```

Compute the mean of the observed values in `X`.

# Examples

```jldoctest
julia> mean_skipmissing([1.0; missing; 3.0])
2.0
```

```
sum_skipmissing(X::AbstractVector{Float64})
sum_skipmissing(X::AbstractVector{Union{Missing, Float64}})
```

Compute the sum of the observed values in `X`.

# Examples

```jldoctest
julia> sum_skipmissing([1.0; missing; 3.0])
4.0
```

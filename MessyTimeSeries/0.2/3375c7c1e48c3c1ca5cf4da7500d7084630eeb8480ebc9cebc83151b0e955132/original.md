```
sum_skipmissing(X::AbstractMatrix{Float64})
sum_skipmissing(X::AbstractMatrix{Union{Missing, Float64}})
```

Compute the sum of the observed values in `X` column wise.

# Examples

```jldoctest
julia> sum_skipmissing([1.0 2.0; missing 3.0; 3.0 5.0])
3-element Array{Float64,1}:
 3.0
 3.0
 8.0
```

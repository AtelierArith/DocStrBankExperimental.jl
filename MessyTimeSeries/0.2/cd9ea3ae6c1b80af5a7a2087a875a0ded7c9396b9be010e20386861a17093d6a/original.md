```
mean_skipmissing(X::AbstractMatrix{Float64})
mean_skipmissing(X::AbstractMatrix{Union{Missing, Float64}})
```

Compute the mean of the observed values in `X` column wise.

# Examples

```jldoctest
julia> mean_skipmissing([1.0 2.0; missing 3.0; 3.0 5.0])
3-element Array{Float64,1}:
 1.5
 3.0
 4.0
```

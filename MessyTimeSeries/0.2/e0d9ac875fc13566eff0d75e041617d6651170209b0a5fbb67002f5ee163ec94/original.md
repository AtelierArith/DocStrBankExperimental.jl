```
std_skipmissing(X::AbstractMatrix{Float64})
std_skipmissing(X::AbstractMatrix{Union{Missing, Float64}})
```

Compute the standard deviation of the observed values in `X` column wise.

# Examples

```jldoctest
julia> std_skipmissing([1.0 2.0; missing 3.0; 3.0 5.0])
3-element Array{Float64,1}:
   0.7071067811865476
 NaN
   1.4142135623730951
```

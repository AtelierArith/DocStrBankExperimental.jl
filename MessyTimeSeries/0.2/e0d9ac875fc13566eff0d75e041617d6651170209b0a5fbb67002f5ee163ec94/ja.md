```
std_skipmissing(X::AbstractMatrix{Float64})
std_skipmissing(X::AbstractMatrix{Union{Missing, Float64}})
```

`X`の観測値の標準偏差を列ごとに計算します。

# 例

```jldoctest
julia> std_skipmissing([1.0 2.0; missing 3.0; 3.0 5.0])
3-element Array{Float64,1}:
   0.7071067811865476
 NaN
   1.4142135623730951
```

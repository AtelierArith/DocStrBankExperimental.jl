```
mean_skipmissing(X::AbstractMatrix{Float64})
mean_skipmissing(X::AbstractMatrix{Union{Missing, Float64}})
```

`X`の観測値の平均を列ごとに計算します。

# 例

```jldoctest
julia> mean_skipmissing([1.0 2.0; missing 3.0; 3.0 5.0])
3-element Array{Float64,1}:
 1.5
 3.0
 4.0
```

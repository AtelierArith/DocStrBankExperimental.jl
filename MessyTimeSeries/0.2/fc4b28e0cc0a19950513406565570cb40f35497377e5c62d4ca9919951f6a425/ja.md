```
mean_skipmissing(X::AbstractVector{Float64})
mean_skipmissing(X::AbstractVector{Union{Missing, Float64}})
```

`X`の観測値の平均を計算します。

# 例

```jldoctest
julia> mean_skipmissing([1.0; missing; 3.0])
2.0
```

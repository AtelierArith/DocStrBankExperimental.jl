```
sum_skipmissing(X::AbstractVector{Float64})
sum_skipmissing(X::AbstractVector{Union{Missing, Float64}})
```

`X`の観測された値の合計を計算します。

# 例

```jldoctest
julia> sum_skipmissing([1.0; missing; 3.0])
4.0
```

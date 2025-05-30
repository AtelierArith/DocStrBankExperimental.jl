```
L₁₋(x̄)
```

`length(x̄)` の `length(x̄) + 2` 行列の離散化された一次微分演算子を、境界条件なしで後方差分を使用して返します。

最初と最後の列は、それぞれ `x̄[1]` の直前と `x̄[end]` の直後のゴーストノードに適用されます。

# 例

```jldoctest; setup = :(using SimpleDifferentialOperators)
julia> x̄ = 1:3
1:3

julia> Array(L₁₋(x̄))
1×3 Array{Float64,2}:
 -1.0  1.0  0.0
```

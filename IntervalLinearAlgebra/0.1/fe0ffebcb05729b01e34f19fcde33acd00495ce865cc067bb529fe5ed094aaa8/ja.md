```
rref(A::AbstractMatrix{T}) where {T<:Interval}
```

区間行列 `A` の縮小行基本形を、最大絶対値をピボット戦略として使用して計算します。

### 例

```jldoctest
julia> A = [2..4 -1..1; -1..1 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-1, 1]
 [-1, 1]   [2, 4]

julia> rref(A)
2×2 Matrix{Interval{Float64}}:
 [2, 4]  [-1, 1]
 [0, 0]       [1.5, 4.5]
```

```
interval_norm(A::AbstractMatrix{T}) where {T<:Interval}
```

は、区間行列 $A$ の無限大ノルムを計算します。

### 例

```jldoctest
julia> A = [2..4 -1..1; -1..1 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-1, 1]
 [-1, 1]   [2, 4]

julia> interval_norm(A)
5.0
```

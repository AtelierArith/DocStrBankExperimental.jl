```
is_M_matrix(A::AbstractMatrix{T}) where {T<:Interval}
```

正方形区間行列 $A$ が M-行列、すなわち非負の逆行列を持つ Z-行列であるかどうかをチェックします。詳細については [[HOR19]](@ref) のセクション 4.2 を参照してください。

### 例

```jldoctest
julia> A = [2..2 -1..0; -1..0 2..2]
2×2 Matrix{Interval{Float64}}:
  [2, 2]  [-1, 0]
 [-1, 0]   [2, 2]

julia> is_M_matrix(A)
true

julia> A = [2..4 -2..1; -1..2 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-2, 1]
 [-1, 2]   [2, 4]

julia> is_M_matrix(A)
false
```

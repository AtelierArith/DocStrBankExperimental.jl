```
is_Z_matrix(A::AbstractMatrix{T}) where {T<:Interval}
```

正方形区間行列 $A$ が Z-行列であるかどうかをチェックします。つまり、すべての $i≠j$ に対して $Aᵢⱼ≤0$ であるかどうかを確認します。詳細については、[[HOR19]](@ref) のセクション 4.2 を参照してください。

### 例

```jldoctest
julia> A = [2..4 -2.. -1; -2.. -1 2..4]
2×2 Matrix{Interval{Float64}}:
   [2, 4]  [-2, -1]
 [-2, -1]    [2, 4]

julia> is_Z_matrix(A)
true

julia> A = [2..4 -2..1; -1..2 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-2, 1]
 [-1, 2]   [2, 4]

julia> is_Z_matrix(A)
false
```

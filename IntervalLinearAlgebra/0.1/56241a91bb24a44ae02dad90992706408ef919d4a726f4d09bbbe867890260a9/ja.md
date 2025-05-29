```
is_strictly_diagonally_dominant(A::AbstractMatrix{T}) where {T<:Interval}
```

正方形の区間行列 $A$ が厳密に対角優位であるかどうかをチェックします。すなわち、$mig(Aᵢᵢ) > ∑_{k ≠ i} mag(Aᵢₖ)$ が $i=1,…,n$ の場合に成り立つかどうかです。詳細については、[[HOR19]](@ref) のセクション 4.5 を参照してください。

### 例

```jldoctest
julia> A = [2..4 -1..1; -1..1 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-1, 1]
 [-1, 1]   [2, 4]

julia> is_strictly_diagonally_dominant(A)
true

julia> A = [2..4 -2..1; -1..2 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-2, 1]
 [-1, 2]   [2, 4]

julia> is_strictly_diagonally_dominant(A)
false
```

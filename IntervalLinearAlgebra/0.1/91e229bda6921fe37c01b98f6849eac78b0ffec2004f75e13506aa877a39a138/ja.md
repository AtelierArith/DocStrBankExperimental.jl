```
comparison_matrix(A::AbstractMatrix{T}) where {T<:Interval}
```

与えられた区間行列 $A$ の比較行列 $⟨A⟩$ を、定義に従って計算します。$⟨A⟩ᵢᵢ = mig(Aᵢᵢ)$ および $⟨A⟩ᵢⱼ = -mag(Aᵢⱼ)$ ただし $i≠j$ の場合です。

### 例

```jldoctest
julia> A = [2..4 -1..1; -1..1 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-1, 1]
 [-1, 1]   [2, 4]

julia> comparison_matrix(A)
2×2 Matrix{Float64}:
  2.0  -1.0
 -1.0   2.0
```

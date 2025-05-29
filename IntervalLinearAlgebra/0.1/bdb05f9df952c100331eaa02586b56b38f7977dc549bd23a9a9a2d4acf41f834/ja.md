```
is_H_matrix(A::AbstractMatrix{T}) where {T<:Interval}
```

正方形区間行列 A が H-行列であるかどうかをテストします。これは $⟨A⟩^{-1}e>0$ をテストすることによって行われ、ここで $e=[1, 1, …, 1]ᵀ$ です。実際には、$⟨A⟩^{-1}e$ の *浮動小数点近似* が条件を満たすかどうかをテストします。詳細については [[HOR19]](@ref) のセクション 4.4 を参照してください。

### 例

```jldoctest
julia> A = [2..4 -1..1; -1..1 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-1, 1]
 [-1, 1]   [2, 4]

julia> is_H_matrix(A)
true

julia> A = [2..4 -2..1; -1..2 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-2, 1]
 [-1, 2]   [2, 4]

julia> is_H_matrix(A)
false
```

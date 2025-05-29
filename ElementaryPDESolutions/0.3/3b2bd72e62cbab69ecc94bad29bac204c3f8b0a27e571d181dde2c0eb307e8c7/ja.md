```
solve_anisotropic_advect_diffuse(A::SMatrix{N, N}, β::AbstractVector{T}, Q::Polynomial)
```

異方性輸送拡散方程 `∇ ⋅ (A ∇P) + β⋅∇P = Q` を満たす多項式 `P` を返します。`A` は対称正定値行列です。

# 例

```jldoctest
using StaticArrays
A = SMatrix{2,2,Rational{Int64}}(2 // 1, 1 // 1, 1 // 1, 3 // 1)
β = SVector{2,Rational{Int64}}(2 // 1, 1 // 1)
Q = Polynomial([(0, 1) => 2 // 1])
P = solve_anisotropic_advect_diffuse(A, β, Q)

# 出力

-14//25y - 28//25x + 16//25xy + 9//25y² - 4//25x²
```

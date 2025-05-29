```
solve_anisotropic_advect(β::AbstractVector, Q::Polynomial)
```

異方性輸送方程 `β⋅∇P = Q` を満たす多項式 `P` を返します。

# 例

```jldoctest
using StaticArrays
β = SVector{2,Rational{Int64}}(2 // 1, 1 // 1)
Q = Polynomial([(0, 0) => 2 // 1])
P = solve_anisotropic_advect(β, Q)

# 出力

2//5y + 4//5x
```

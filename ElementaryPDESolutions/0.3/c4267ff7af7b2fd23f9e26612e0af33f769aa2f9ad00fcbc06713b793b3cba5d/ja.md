```
solve_anisotropic_laplace(A::AbstractMatrix{T}, Q::Polynomial)
```

非各向同性ラプラス方程式 `∇ ⋅ (A ∇P) = Q` を満たす多項式 `P` を返します。ここで、`A` は可逆行列であり、`Q` は同次である必要があります。逆行列は [`anisotropic_laplacian`](@ref) です。

# 例

```jldoctest
using StaticArrays
A = SMatrix{2,2,Rational{Int64}}(2 // 1, 1 // 1, 1 // 1, 3 // 1)
Q = Polynomial([(1, 1) => 2 // 1])
P = solve_anisotropic_laplace(A, Q)

# 出力

-3//400x⁴ + 11//100x³y + 11//150xy³ - 2//25x²y² - 1//300y⁴
```

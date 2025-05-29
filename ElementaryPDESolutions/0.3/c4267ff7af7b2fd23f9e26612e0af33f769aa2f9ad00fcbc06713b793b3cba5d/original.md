```
solve_anisotropic_laplace(A::AbstractMatrix{T}, Q::Polynomial)
```

Return a polynomial `P` satisfying the anisotropic Laplace equation `∇ ⋅ (A ∇P) = Q`, `A` an invertible matrix. `Q` is required to be homogeneous. Inverse is [`anisotropic_laplacian`](@ref).

# Examples

```jldoctest
using StaticArrays
A = SMatrix{2,2,Rational{Int64}}(2 // 1, 1 // 1, 1 // 1, 3 // 1)
Q = Polynomial([(1, 1) => 2 // 1])
P = solve_anisotropic_laplace(A, Q)

# output

-3//400x⁴ + 11//100x³y + 11//150xy³ - 2//25x²y² - 1//300y⁴
```

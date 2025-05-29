```
solve_anisotropic_advect_diffuse(A::SMatrix{N, N}, β::AbstractVector{T}, Q::Polynomial)
```

Return a polynomial `P` satisfying the anisotropic advection-diffusion equation `∇ ⋅ (A ∇P) + β⋅∇P = Q`, `A` a symmetric positive definite matrix.

# Examples

```jldoctest
using StaticArrays
A = SMatrix{2,2,Rational{Int64}}(2 // 1, 1 // 1, 1 // 1, 3 // 1)
β = SVector{2,Rational{Int64}}(2 // 1, 1 // 1)
Q = Polynomial([(0, 1) => 2 // 1])
P = solve_anisotropic_advect_diffuse(A, β, Q)

# output

-14//25y - 28//25x + 16//25xy + 9//25y² - 4//25x²
```

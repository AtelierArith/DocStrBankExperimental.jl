```
solve_anisotropic_advect(β::AbstractVector, Q::Polynomial)
```

Return a polynomial `P` satisfying the anisotropic advection equation `β⋅∇P = Q`.

# Examples

```jldoctest
using StaticArrays
β = SVector{2,Rational{Int64}}(2 // 1, 1 // 1)
Q = Polynomial([(0, 0) => 2 // 1])
P = solve_anisotropic_advect(β, Q)

# output

2//5y + 4//5x
```

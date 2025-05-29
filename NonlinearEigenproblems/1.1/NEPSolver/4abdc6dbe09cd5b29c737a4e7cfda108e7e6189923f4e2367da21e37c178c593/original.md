```
struct PolyeigInnerSolver <: InnerSolver
function PolyeigInnerSolver()
```

Specifies the use of [`polyeig`](@ref) to solve the inner problem. This is intended for NEPs of the type [`PEP`](@ref).

See also: [`InnerSolver`](@ref), [`inner_solve`](@ref)

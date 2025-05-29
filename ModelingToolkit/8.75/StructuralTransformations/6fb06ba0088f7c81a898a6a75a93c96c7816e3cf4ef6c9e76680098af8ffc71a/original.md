```
ODAEProblem{iip}(sys, u0map, tspan, parammap = DiffEqBase.NullParameters(); kw...)
```

This constructor acts similar to the one for [`ODEProblem`](@ref) with the following changes: `ODESystem`s can sometimes be further reduced if `structural_simplify` has already been applied to them. In these cases, the constructor uses the knowledge of the strongly connected components calculated during the process of simplification as the basis for building pre-simplified nonlinear systems in the implicit solving.

In summary: these problems are structurally modified, but could be more efficient and more stable. Note, the returned object is still of type [`ODEProblem`](@ref).

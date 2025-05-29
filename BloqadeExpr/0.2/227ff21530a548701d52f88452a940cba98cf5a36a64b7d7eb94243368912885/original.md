```
struct SumOfXPhase <: AbstractTerm{2}
SumOfXPhase(;nsites, Ω=1, ϕ)
```

Sum of `XPhase` operators.

The following two expressions are equivalent

```jldoctest; setup=:(using BloqadeExpr)
julia> SumOfXPhase(nsites=5, ϕ=0.1)
1.0 ⋅ ∑ e^{0.1 ⋅ im} |0⟩⟨1| + e^{-0.1 ⋅ im} |1⟩⟨0|

julia> sum([XPhase(0.1) for _ in 1:5])
nqudits: 1
+
├─ XPhase(0.1)
├─ XPhase(0.1)
├─ XPhase(0.1)
├─ XPhase(0.1)
└─ XPhase(0.1)
```

But may provide extra speed up.

# Expression

$$
\sum_i Ω ⋅ (e^{ϕ ⋅ i} |0⟩⟨1| + e^{-ϕ ⋅ i} |1⟩⟨0|)
$$

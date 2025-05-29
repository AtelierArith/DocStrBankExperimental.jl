```
struct SumOfXPhase_01 <: AbstractTerm{3}
SumOfXPhase_01(nsites, Ω, ϕ)
```

Term for sum of `XPhase_01` operators.

# Expression

$$
\sum_i Ω ⋅ (e^{ϕ ⋅ i} |0⟩⟨1| + e^{-ϕ ⋅ i} |1⟩⟨0|)
$$

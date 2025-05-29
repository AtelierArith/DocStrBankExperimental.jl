```
struct SumOfXPhase_1r <: AbstractTerm{3}
SumOfXPhase_1r(nsites, Ω, ϕ)
```

Term for sum of `XPhase_1r` operators.

# Expression

$$
\sum_i Ω ⋅ (e^{ϕ ⋅ i} |1⟩⟨r| + e^{-ϕ ⋅ i} |r⟩⟨1|)
$$

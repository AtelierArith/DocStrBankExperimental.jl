```
struct SumOfXPhase_01 <: AbstractTerm{3}
SumOfXPhase_01(nsites, Ω, ϕ)
```

`XPhase_01` 演算子の和の項。

# 表現

$$
\sum_i Ω ⋅ (e^{ϕ ⋅ i} |0⟩⟨1| + e^{-ϕ ⋅ i} |1⟩⟨0|)
$$

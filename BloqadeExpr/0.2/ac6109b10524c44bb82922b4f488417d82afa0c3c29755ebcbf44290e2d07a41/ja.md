```
struct SumOfXPhase_1r <: AbstractTerm{3}
SumOfXPhase_1r(nsites, Ω, ϕ)
```

`XPhase_1r` 演算子の和の項。

# 表現

$$
\sum_i Ω ⋅ (e^{ϕ ⋅ i} |1⟩⟨r| + e^{-ϕ ⋅ i} |r⟩⟨1|)
$$

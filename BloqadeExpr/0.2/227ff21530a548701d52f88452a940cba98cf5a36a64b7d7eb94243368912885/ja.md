```
struct SumOfXPhase <: AbstractTerm{2}
SumOfXPhase(;nsites, Ω=1, ϕ)
```

`XPhase` 演算子の合計。

以下の二つの式は同等です。

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

しかし、追加のスピードアップを提供する可能性があります。

# 表現

$$
\sum_i Ω ⋅ (e^{ϕ ⋅ i} |0⟩⟨1| + e^{-ϕ ⋅ i} |1⟩⟨0|)
$$

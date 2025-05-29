```
struct SumOfX <: AbstractTerm{2}
SumOfX(nsites, Ω)
```

X演算子の和の項。

次の2つの式は同等です。

```jldoctest; setup=:(using BloqadeExpr, YaoBlocks)
julia> SumOfX(nsites=5)
∑ σ^x_i

julia> sum([X for _ in 1:5])
nqudits: 1
+
├─ X
├─ X
├─ X
├─ X
└─ X
```

# 表現

$$
\sum_i Ω σ^x_i
$$

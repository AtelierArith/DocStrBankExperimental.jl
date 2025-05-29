```
struct SumOfN <: AbstractTerm{2}
SumOfN(;nsites[, Δ=1])
```

N演算子の合計。

次の2つの式は同等です。

```jldoctest; setup=:(using BloqadeExpr)
julia> SumOfN(nsites=5)
∑ n_i

julia> sum([Op.n for _ in 1:5])
nqudits: 1
+
├─ P1
├─ P1
├─ P1
├─ P1
└─ P1
```

しかし、追加のスピードアップを提供する可能性があります。

# 表現

$$
\sum_i Δ ⋅ n_i
$$

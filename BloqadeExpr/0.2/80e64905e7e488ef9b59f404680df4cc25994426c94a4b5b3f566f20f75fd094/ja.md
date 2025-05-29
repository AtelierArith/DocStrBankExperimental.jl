```
struct SumOfZ <: AbstractTerm{2}
SumOfZ(;nsites, Δ=1)
```

パウリ Z 演算子の和。

次の二つの表現は同等です。

```jldoctest; setup=:(using BloqadeExpr, YaoBlocks)
julia> SumOfZ(nsites=5)
∑ σ^z_i

julia> sum([Z for _ in 1:5])
nqudits: 1
+
├─ Z
├─ Z
├─ Z
├─ Z
└─ Z
```

# 表現

$$
\sum_i Δ ⋅ σ^z_i
$$

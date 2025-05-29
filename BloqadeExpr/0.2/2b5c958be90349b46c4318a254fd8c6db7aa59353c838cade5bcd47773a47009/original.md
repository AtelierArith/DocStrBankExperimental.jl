```
struct SumOfN <: AbstractTerm{2}
SumOfN(;nsites[, Δ=1])
```

Sum of N operators. 

The following two expression are equivalent

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

But may provide extra speed up.

# Expression

$$
\sum_i Δ ⋅ n_i
$$

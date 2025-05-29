```
struct SumOfX <: AbstractTerm{2}
SumOfX(nsites, Ω)
```

Term for sum of X operators.

The following two expressions are equivalent

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

# Expression

$$
\sum_i Ω σ^x_i
$$

```
struct SumOfZ <: AbstractTerm{2}
SumOfZ(;nsites, Δ=1)
```

Sum of Pauli Z operators.

The following two expression are equivalent

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

# Expression

$$
\sum_i Δ ⋅ σ^z_i
$$

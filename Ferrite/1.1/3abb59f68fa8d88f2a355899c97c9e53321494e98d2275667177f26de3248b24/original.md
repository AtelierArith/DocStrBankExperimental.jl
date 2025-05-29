```
AffineConstraint(constrained_dof::Int, entries::Vector{Pair{Int,T}}, b::T) where T
```

Define an affine/linear constraint to constrain one degree of freedom, `u[i]`, such that `u[i] = ∑(u[j] * a[j]) + b`, where `i=constrained_dof` and each element in `entries` are `j => a[j]`

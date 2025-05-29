```
getdof(μ)
```

Returns the effective number of degrees of freedom of variates of measure `μ`.

The effective NDOF my differ from the length of the variates. For example, the effective NDOF for a Dirichlet distribution with variates of length `n` is `n - 1`.

Also see [`check_dof`](@ref).

```julia
AltMvNormal(_, μ, L)

```

Inner constructor used internally, for specifying `L` directly when the first argument is `Val{:L}`.

You **don't want to use this unless you obtain `L` directly**. Use a `Cholesky` factorization instead.

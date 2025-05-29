```
JacobianFreeJVP
```

Computes the Jacobian-vector product `j(x[n]) * Δx[n]` for a Newton-Krylov method without directly using the Jacobian `j(x[n])`, and instead only using `x[n]`, `f(x[n])`, and other function evaluations `f(x′)`. This is done by calling `jvp!(::JacobianFreeJVP, cache, jΔx, Δx, x, f!, f, prepare_for_f!)`. The `jΔx` passed to a Jacobian-free JVP is modified in-place. The `cache` can be obtained with `allocate_cache(::JacobianFreeJVP, x_prototype)`, where `x_prototype` is `similar` to `x` (and also to `Δx` and `f`).

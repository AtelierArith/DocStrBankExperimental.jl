```
SymbolicsSparsityDetector <: ADTypes.AbstractSparsityDetector
```

Sparsity detection algorithm based on the [Symbolics.jl tracing system](https://symbolics.juliasymbolics.org/stable/manual/sparsity_detection/).

This type makes Symbolics.jl compatible with the [ADTypes.jl sparsity detection framework](https://sciml.github.io/ADTypes.jl/stable/#Sparsity-detector). The following functions are implemented:

  * `ADTypes.jacobian_sparsity` based on [`Symbolics.jacobian_sparsity`](@ref)
  * `ADTypes.hessian_sparsity` based on [`Symbolics.hessian_sparsity`](@ref)

# Reference

> [Sparsity Programming: Automated Sparsity-Aware Optimizations in Differentiable Programming](https://openreview.net/forum?id=rJlPdcY38B), Gowda et al. (2019)


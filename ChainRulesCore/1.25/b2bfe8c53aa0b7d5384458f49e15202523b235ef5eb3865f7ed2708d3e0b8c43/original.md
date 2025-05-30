```
AbstractZero <: AbstractTangent
```

Supertype for zero-like tangents—i.e., tangents that act like zero when added or multiplied to other values. If an AD system encounters a propagator that takes as input only subtypes of `AbstractZero`, then it can stop performing AD operations. All propagators are linear functions, and thus the final result will be zero.

All `AbstractZero` subtypes are singleton types. There are two of them: [`ZeroTangent()`](@ref) and [`NoTangent()`](@ref).

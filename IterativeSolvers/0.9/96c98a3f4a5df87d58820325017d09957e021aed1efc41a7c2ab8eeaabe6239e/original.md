```
invpowm!(B, x0; shift = σ, kwargs...) -> λ, x, [history]
```

Find the approximate eigenpair `(λ, x)` of $A$ near `shift`, where `B` is a linear map that has the effect `B * v = inv(A - σI) * v`.

The method calls `powm!(B, x0; inverse = true, shift = σ)`. See [`powm!`](@ref).

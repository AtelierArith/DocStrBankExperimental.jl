```
jacobian(F, mₒ)
```

Return the jacobian of `F::Union{Jet, Jop, AbstractMatrix}` at the point `m₀`. The linearization constructs a new underlying `Jet`.

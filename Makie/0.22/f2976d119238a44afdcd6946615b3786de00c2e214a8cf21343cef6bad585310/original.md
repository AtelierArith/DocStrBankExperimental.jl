```
ReversibleScale
```

Custom scale struct, taking a forward and inverse arbitrary scale function.

## Fields

  * `forward::Function`: forward transformation (e.g. `log10`)

  * `inverse::Function`: inverse transformation (e.g. `exp10` for `log10` such that inverse ∘ forward ≡ identity)

  * `limits::Tuple{Float32, Float32}`: default limits (optional)

  * `interval::IntervalSets.AbstractInterval`: valid limits interval (optional)

  * `name::Symbol`

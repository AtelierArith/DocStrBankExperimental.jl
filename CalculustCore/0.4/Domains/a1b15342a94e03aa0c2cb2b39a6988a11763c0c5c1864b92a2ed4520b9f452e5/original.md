```julia
deform(domain; ...)
deform(domain, mapping; isseparable, isrescaling)

```

Deform `domain` via `mapping`, which expects the function signature

```
mapping(r1, ..., rD) = x1, ..., xD
```

where the inputs and outputs are `NTuple{D, <:AbstractArray}`.

# Keyword Arguments

  * `isrescaling` - Set to `true` if `mapping` is a rescaling operation, i.e.

    x1 = a1 + λ1 × x1(r1),

    ...,

    xD = aD + λD × xD(rD)
  * `isseparable` - Set to `true` if `mapping` is separable, i.e.

    x1 = x1(r1),

    ...,

    xD = xD(rD)

TODO - make types for AffineMap, LinearMap, SeparableMap, Transation, Rotation TODO - check `static_hasmethod` in constructor

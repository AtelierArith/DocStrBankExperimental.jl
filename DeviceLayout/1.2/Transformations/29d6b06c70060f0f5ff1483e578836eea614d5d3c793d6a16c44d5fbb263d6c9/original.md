```
struct ScaledIsometry{T<:Union{Point, Nothing}} <: AbstractAffineMap
ScaledIsometry(origin=nothing, rotation=0°, xrefl=false, mag=1.0)
```

A coordinate transformation that preserves angles.

The equivalent transformation of `f::ScaledIsometry` is the composition of the following transformations, ordered with reflection applied first:

1. If `xrefl(f)` is `true`, a reflection across the `x`-axis
2. Rotation by `rotation(f)`
3. Magnification by `mag(f)`
4. Translation by `origin(f)`

May be also be constructed as

```julia
ScaledIsometry(f::Transformation) = ScaledIsometry(origin(f), rotation(f), xrefl(f), mag(f))
```

but a `DomainError` will be thrown if `f` is not a scaled isometry (does not preserve angles).

`Transformation` compositions (with `compose` or `∘`) involving a `ScaledIsometry` will return a `ScaledIsometry` if the other transformation also preserves angles.

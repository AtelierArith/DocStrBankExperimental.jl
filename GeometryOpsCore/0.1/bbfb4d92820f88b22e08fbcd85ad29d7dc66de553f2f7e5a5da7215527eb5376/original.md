```
TraitTarget{T}
```

This struct holds a trait parameter or a union of trait parameters.

It is primarily used for dispatch into methods which select trait levels,  like `apply`, or as a parameter to `target`.

## Constructors

```julia
TraitTarget(GI.PointTrait())
TraitTarget(GI.LineStringTrait(), GI.LinearRingTrait()) # and other traits as you may like
TraitTarget(TraitTarget(...))
# There are also type based constructors available, but that's not advised.
TraitTarget(GI.PointTrait)
TraitTarget(Union{GI.LineStringTrait, GI.LinearRingTrait})
# etc.
```

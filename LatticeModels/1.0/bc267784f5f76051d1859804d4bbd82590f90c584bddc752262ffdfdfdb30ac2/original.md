```
TwistedBoundary <: Boundary
```

A boundary condition with a phase twist. A `PeriodicBoundary` is a special case of `TwistedBoundary` with zero twist.

---

```
TwistedBoundary(translation, Θ)
```

Construct a `TwistedBoundary` with a given translation and twist angle.

## Arguments

  * `translation`: The translation vector of the boundary representad as `AbstractTranslation`.   If an array is passed, it is converted to `Translation` automatically.
  * `Θ`: The twist angle in radians.

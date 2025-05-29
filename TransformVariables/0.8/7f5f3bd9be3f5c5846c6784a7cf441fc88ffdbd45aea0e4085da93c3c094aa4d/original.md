```
inverse_eltype(t::AbstractTransform, y)
```

The element type for vector `x` so that `inverse!(x, t, y)` works.

!!! note
    It is not guaranteed that the result is the narrowest possible type, and may change without warning between versions. Some effort is made to come up with a reasonable concrete type even in corner cases.


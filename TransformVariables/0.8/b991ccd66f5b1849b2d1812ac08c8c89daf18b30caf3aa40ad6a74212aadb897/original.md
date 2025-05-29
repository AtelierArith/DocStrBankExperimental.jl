```
inverse(t, y)
```

Return `x` so that `transform(t, x) ≈ y`.

```
inverse(t)
```

Return a callable equivalent to `y -> inverse(t, y)`. `t` can also be a callable created with transform, so the following holds:

```julia
inverse(t)(y) == inverse(t, y) == inverse(transform(t))(y)
```

!!! note
    `eltype(inverse(t, transform(t, x)))` is not necessarily equal to `eltype(x)`, it is not guaranteed to be the narrowest possible type, and may change without warning between versions. Some effort is made to come up with a reasonable concrete type even in corner cases.


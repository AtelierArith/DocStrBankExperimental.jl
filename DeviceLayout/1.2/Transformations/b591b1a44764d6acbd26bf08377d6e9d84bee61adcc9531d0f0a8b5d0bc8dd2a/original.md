```
rotation(f::Transformation; α0=0)
```

Return the change in angle when applying `f` to a line originally at `α0` CCW from the `x`-axis.

By default, `α0` is taken to be `0`, and the result is equivalent to the rotation when decomposing the linear part of `f` into reflection across the `x`-axis followed by rotation.

Units are accepted for `α0` (no units => radians).

If `f` does not preserve angles, a `DomainError` is thrown.

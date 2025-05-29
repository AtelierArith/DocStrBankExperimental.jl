```
transformation(h1::Hook, h2::Hook)
```

Return a `CoordinateTransformation` to align `h2` to `h1`.

Given hooks `h1, h2` relative to  `CoordinateSystem`s `h1cs, h2cs` respectively, if you reference `h2cs` inside `h1cs` with `push!(h1cs.refs, sref(h2cs, origin, rot=rotation, xrefl=xrefl))`, then relative to `h1cs`, `h2` will lie on top of `h1` with its `in_direction` pointing opposite to that of `h1` (and matching handedness, if applicable).

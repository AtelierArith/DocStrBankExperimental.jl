```
RotationPi(Θ_over_pi=1; around_pt=nothing)
```

Construct a rotation about the origin or `around_pt`, with rotation in units of `pi` (`180°`).

This may be useful if you know your rotation will be a multiple of 90° but not necessarily which one, since it can be slightly more precise than `Rotation` (as `sincospi` is to `sincos`).

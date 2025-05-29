```
profile(m::LinearMixedModel; threshold = 4)
```

Return a `MixedModelProfile` for the objective of `m` with respect to the fixed-effects coefficients.

`m` is `refit!` if `!isfitted(m)`.

Profiling starts at the parameter estimate and continues until reaching a parameter bound or the absolute value of ζ exceeds `threshold`.

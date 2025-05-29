```
plan_helmholtz!(dims::Tuple,α::Number,[with_inverse=false],[fftw_flags=FFTW.ESTIMATE],
                      [factor=1.0],[dx=1.0])
```

Same as [`plan_helmholtz`](@ref), but forms an operator that works in-place on the data it operates on.

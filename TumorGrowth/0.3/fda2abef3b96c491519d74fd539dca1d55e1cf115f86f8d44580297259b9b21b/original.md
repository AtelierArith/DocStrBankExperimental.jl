```
CalibrationProblem(problem; kwargs...)
```

Construct a new calibration problem out an existing `problem` but supply new keyword arguments, `kwargs`. Unspecified keyword arguments fall back to defaults, except for `p0`, which falls back to `solution(problem)`.

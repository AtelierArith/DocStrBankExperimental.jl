```
solve!(problem, n)
```

Solve a calibration `problem`, as constructed with [`CalibrationProblem`](@ref). The calibrated parameters are then returned by `solution(problem)`.

If using a Gauss-Newton optimiser (`LevenbergMarquardt` or `Dogleg`) specify `n=0` to choose `n` automatically.

---

```
solve!(problem, controls...)
```

Solve a calibration `problem` using one or more iteration `controls`, from the package IterationControls.jl. See the "Extended help" section of [`CalibrationProblem`](@ref) for examples.

Not recommended for Gauss-Newton optimisers (`LevenbergMarquardt` or `Dogleg`).

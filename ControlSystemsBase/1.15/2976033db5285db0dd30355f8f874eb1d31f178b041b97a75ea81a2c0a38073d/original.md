```
lyap(A, Q; kwargs...)
```

Compute the solution `X` to the discrete Lyapunov equation `AXA' - X + Q = 0`.

Uses `MatrixEquations.lyapc / MatrixEquations.lyapd`. For keyword arguments, see the docstring of `ControlSystemsBase.MatrixEquations.lyapc / ControlSystemsBase.MatrixEquations.lyapd`

```
are(::Discrete, A, B, Q, R; kwargs...)
```

Compute `X`, the solution to the discrete-time algebraic Riccati equation, defined as A'XA - X - (A'XB)(B'XB + R)^-1(B'XA) + Q = 0, where Q>=0 and R>0

In an LQR problem, `Q` is associated with the state penalty $x'Qx$ while `R` is associated with the control penalty $u'Ru$. See [`lqr`](@ref) for more details.

Uses `MatrixEquations.ared`. For keyword arguments, see the docstring of `ControlSystemsBase.MatrixEquations.ared`, note that they define the input arguments in a different order.

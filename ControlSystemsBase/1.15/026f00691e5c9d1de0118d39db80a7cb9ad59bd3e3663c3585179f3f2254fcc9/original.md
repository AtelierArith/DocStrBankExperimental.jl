```
are(::Continuous, A, B, Q, R)
```

Compute 'X', the solution to the continuous-time algebraic Riccati equation, defined as A'X + XA - (XB)R^-1(B'X) + Q = 0, where R is non-singular.

In an LQR problem, `Q` is associated with the state penalty $x'Qx$ while `R` is associated with the control penalty $u'Ru$. See [`lqr`](@ref) for more details.

Uses `MatrixEquations.arec`. For keyword arguments, see the docstring of `ControlSystemsBase.MatrixEquations.arec`, note that they define the input arguments in a different order.

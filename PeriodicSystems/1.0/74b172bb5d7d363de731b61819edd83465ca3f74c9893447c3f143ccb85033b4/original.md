```
 pckeg(psys, Qw, Rv, Sn; intpol = true, kwargs...) -> (L, EVALS)
```

Compute the Kalman estimator periodic gain matrix `L(t)` for a continuous-time periodic state-space model  `psys` of the form

```
  .
  x(t) = A(t)x(t) + B(t)u(t) + w(t)
  y(t) = C(t)x(t) + D(t)u(t) + v(t)
```

and the noise covariance data `E{w(t)w(t)'} = Qw(t)`, `E{v(t)v(t)'} = Rv(t)`, `E{w(t)v(t)'} = Sn(t)`,  for a Kalman estimator 

```
   .
  xe(t) = A(t)xe(t) + B(t)u(t) + L(t)(y(t)-C(t)xe(t)-D(t)u(t))
```

For a system of order `n` with `p` outputs, `Qw` and `Rv` are `n×n` and `p×p` symmetric matrices, respectively, and `Sn` is an `n×p` matrix.                 `Qw`, `Rv` and `Sn` can be alternatively provided as constant real matrices.  The matrix `Sn` is set to zero when omitted. 

Also returned are the closed-loop characteristic exponents `EVALS` of `A(t)-L(t)C(t)`.

For `intpol = true` (default), the resulting periodic gain `L(t)` is computed from the  stabilizing solution of a continuous-time periodic matrix differential Riccati equation using interpolation based formulas.  If `intpol = false`, the gain `L(t)` is computed from a multi-point solution of the Riccati differential equation  by the integration of the corresponding ODE using the nearest point value as initial condition.  This option is not recommended to be used jointly with symplectic integrators, which are used by default.   

The keyword arguments contained in `kwargs` are those used for the function [`PeriodicMatrixEquations.pfcric`](@extref) (excepting intpol). 

Note: The pair `(A(t),C(t))` must be detectable and `[Qw Sn;Sn' Rv]` must be nonnegative definite.

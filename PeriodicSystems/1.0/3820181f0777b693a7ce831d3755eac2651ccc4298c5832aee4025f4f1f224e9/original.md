```
 pdkegw(psys, Qw, Rv, Sn; kwargs...) -> (L, EVALS)
```

Compute the Kalman estimator periodic gain matrix `L(t)` for a discrete-time periodic state-space model  `psys` of the form

```
x(t+1) = A(t)x(t) + B(t)u(t) + Bw(t)w(t)
  y(t) = C(t)x(t) + D(t)u(t) + Dw(t)w(t) + v(t)
```

and the noise covariance data `E{w(t)w(t)'} = Qw(t)`, `E{v(t)v(t)'} = Rv(t)`, `E{w(t)v(t)'} = Sn(t)`,  for a Kalman estimator 

```
  xe(t+1) = A(t)xe(t) + B(t)u(t) + L(t)(y(t)-C(t)xe(t)-D(t)u(t))
```

For a system with `mw` disturbance inputs and `p` outputs, `Qw` and `Rv` are `mw×mw` and `p×p` symmetric matrices, respectively, and `Sn` is an `mw×p` matrix.   `Qw`, `Rv` and `Sn` can be alternatively provided as constant real matrices.                The matrix `Sn` is set to zero when omitted. The number of disturbance inputs `mw` is defined by the order of matrix `Qw`. 

Also returned are the closed-loop characteristic exponents `EVALS` of `A(t)-L(t)C(t)`.

The keyword arguments contained in `kwargs` are those used for the function [`PeriodicMatrixEquations.pfdric`](@extref). 

Note: The pair `(A(t),C(t))` must be detectable,  `Qw` must be non-negative definite,  `Rv` must be positive definite and `[Qw Sn; Sn' Rv]` must be nonnegative definite.

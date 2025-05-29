```
 pclqry(psys, Q, R, S; intpol = true, kwargs...) -> (F, EVALS)
```

Compute the optimal periodic stabilizing gain matrix F(t), such that for a periodic  continuous-time state-space model `psys` of the form        .       x(t) = A(t)x(t) + B(t)u(t) + Bw(t)w(t)        y(t) = C(t)x(t) + D(t)u(t) + Dw(t)w(t) ,

the state feedback control law

```
 u(t) = F(t)x(t)
```

minimizes the quadratic index

```
 J = Integral {y'(t)Q(t)y(t) + u'(t)R(t)u(t) + 2*y'(t)S(t)u(t)} dt
```

For a system with `m` control inputs `u(t)` and `p` outputs, `Q(t)` and `R(t)` are `p×p` and `m×m` symmetric matrices, respectively, and `S(t)` is an `p×m` matrix.  The dimension of `u(t)` is deduced from the dimension of `R(t)`.  `R`, `Q` and `S` can be alternatively provided as constant real matrices.                              The matrix `S` is set to zero when omitted. 

Also returned are the closed-loop characteristic exponents `EVALS` of `A(t)+B(t)F(t)`.

For `intpol = true` (default), the resulting periodic gain `F(t)` is computed from the  stabilizing solution of a continuous-time periodic matrix differential Riccati equation using interpolation based formulas.  If `intpol = false`, the gain `F(t)` is computed from a multi-point solution of the Riccati differential equation  by the integration of the corresponding ODE using the nearest point value as initial condition.  This option is not recommended to be used jointly with symplectic integrators, which are used by default.   

The keyword arguments contained in `kwargs` are those used for the function [`PeriodicMatrixEquations.prcric`](@extref) (excepting intpol).  

Note: The pair `(A(t),B(t))` must be stabilizable and `[Q S;S' R]` must be nonnegative definite.

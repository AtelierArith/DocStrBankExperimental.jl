```
 pdlqr(psys, Q, R, S; kwargs...) -> (F, EVALS)
```

Compute the optimal periodic stabilizing gain matrix `F(t)`, such that for a discrete-time periodic state-space model  `psys` of the form

```
x(t+1) = A(t)x(t) + B(t)u(t) + Bw(t)w(t) 
  y(t) = C(t)x(t) + D(t)u(t) + Dw(t)w(t)
```

the state feedback control law

```
 u(t) = F(t)x(t)
```

minimizes the quadratic index

```
 J = Sum {x'(t)Q(t)x(t) + u'(t)R(t)u(t) + 2*x'(t)S(t)u(t)}
```

For a system of order `n(t)` with `m` control inputs in `u(t)`, `Q(t)` and `R(t)` are `n(t)×n(t)` and `m×m` symmetric matrices, respectively, and `S(t)` is an `n(t)×m` matrix.                 The matrix `S` is set to zero when omitted. The dimension of `u(t)` is deduced from the dimension of `R(t)`.  `R`, `Q` and `S` can be alternatively provided as constant real matrices. 

Also returned are the closed-loop characteristic exponents `EVALS` of `A(t)+B(t)F(t)`.

The keyword arguments contained in `kwargs` are those used for the function  [`PeriodicMatrixEquations.prdric`](@extref).

Note: The pair `(A(t),B(t))` must be stabilizable and `[Q S;S' R]` must be nonnegative definite.

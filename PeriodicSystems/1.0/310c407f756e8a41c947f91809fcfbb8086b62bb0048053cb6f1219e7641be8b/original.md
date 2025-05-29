```
 pdlqry(psys, Q, R, S; kwargs...) -> (F, EVALS)
```

Compute the optimal periodic stabilizing gain matrix `F(t)`, such that for a periodic discrete-time  state-space model `psys` of the form

```
x(t+1) = A(t)x(t) + B(t)u(t) + Bw(t)w(t)
  y(t) = C(t)x(t) + D(t)u(t) + Dw(t)w(t),
```

the state feedback control law

```
 u(t) = F(t)x(t)
```

minimizes the quadratic index

```
 J = Sum {y'(t)Q(t)y(t) + u'(t)R(t)u(t) + 2*y'(t)S(t)u(t)}
```

For a system with `m` control inputs `u(t)` and `p` outputs, `Q(t)` and `R(t)` are `p×p` and `m×m` symmetric matrices, respectively, and `S(t)` is a `p×m` matrix.   The dimension of `u(t)` is deduced from the dimension of `R(t)`.  `R`, `Q` and `S` can be alternatively provided as constant real matrices.                The matrix `S` is set to zero when omitted. 

Also returned are the closed-loop characteristic exponents `EVALS` of `A(t)+B(t)F(t)`.

The keyword arguments contained in `kwargs` are those used for the function [`PeriodicMatrixEquations.prdric`](@extref). 

Note: The pair `(A(t),B(t))` must be stabilizable and `[Q S;S' R]` must be nonnegative definite.

```
AdditiveRungeKuttaMethod(rks)
AdditiveRungeKuttaMethod(As, bs, cs=map(A -> vec(sum(A, dims=2)), As))
```

Represent an additive Runge-Kutta method with collections of Butcher coefficients `As`, `bs`, and `cs`. Alternatively, you can pass a collection of [`RungeKuttaMethod`](@ref)s to the constructor. If the `cs` are not provided, the usual "row sum" requirement of consistency with autonomous problems is applied.

An additive Runge-Kutta method applied to the ODE problem

$$
  u'(t) = \sum_\nu f^\nu(t, u(t))
$$

has the form

$$
\begin{aligned}
  y^i &= u^n + \Delta t \sum_\nu \sum_j a^\nu_{i,j} f^\nu(y^i), \\
  u^{n+1} &= u^n + \Delta t \sum_\nu \sum_i b^\nu_{i} f^\nu(y^i).
\end{aligned}
$$

In particular, additive Runge-Kutta methods are a superset of partitioned RK methods, which are applied to partitioned problems of the form

$$
  (u^1)'(t) = f^1(t, u^1, u^2),
  \quad
  (u^2)'(t) = f^2(t, u^1, u^2).
$$

# References

  * A. L. Araujo, A. Murua, and J. M. Sanz-Serna. "Symplectic Methods Based on Decompositions". SIAM Journal on Numerical Analysis 34.5 (1997): 1926-1947. [DOI: 10.1137/S0036142995292128](https://doi.org/10.1137/S0036142995292128)

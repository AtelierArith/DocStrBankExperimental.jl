```
SymmetricLinearSystemObjective{E<:AbstractEvaluationType,TA,T} <: AbstractManifoldObjective{E}
```

Model the objective

$$
f(X) = \frac{1}{2} \lVert \mathcal A[X] + b \rVert_p^2,\qquad X ∈ T_p\mathcal M,
$$

defined on the tangent space $T_p\mathcal M$ at $p$ on the manifold $\mathcal M$.

In other words this is an objective to solve $\mathcal A(p)[X] = -b(p)$ for some linear symmetric operator and a vector function. Note the minus on the right hand side, which makes this objective especially tailored for (iteratively) solving Newton-like equations.

# Fields

  * `A!!`: a symmetric, linear operator on the tangent space
  * `b!!`: a gradient function

where `A!!` can work as an allocating operator `(M, p, X) -> Y` or an in-place one `(M, Y, p, X) -> Y`, and similarly `b!!` can either be a function `(M, p) -> X` or `(M, X, p) -> X`. The first variants allocate for the result, the second variants work in-place.

# Constructor

```
SymmetricLinearSystemObjective(A, b; evaluation=AllocatingEvaluation())
```

Generate the objective specifying whether the two parts work allocating or in-place.

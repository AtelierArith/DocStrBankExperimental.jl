```
StopWhenFirstOrderProgress <: StoppingCriterion
```

A stopping criterion related to the Riemannian adaptive regularization with cubics (ARC) solver indicating that the model function at the current (outer) iterate,

$$
    m(X) = f(p) + <X, \operatorname{grad}f(p)>
      + \frac{1}{2} <X, \operatorname{Hess} f(p)[X]> +  \frac{σ}{3} \lVert X \rVert^3,
$$

defined on the tangent space $T_{p}\mathcal M$ fulfills at the current iterate $X_k$ that

$$
m(X_k) \leq m(0)
\quad\text{ and }\quad
\lVert \operatorname{grad} m(X_k) \rVert ≤ θ \lVert X_k \rVert^2
$$

# Fields

  * `θ`:      the factor $θ$ in the second condition
  * `at_iteration`: indicates at which iteration (including `i=0`) the stopping criterion was fulfilled and is `-1` while it is not fulfilled.

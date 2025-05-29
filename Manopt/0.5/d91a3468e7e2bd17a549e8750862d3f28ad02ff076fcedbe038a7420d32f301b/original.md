```
StopWhenFirstOrderProgress <: StoppingCriterion
```

A stopping criterion related to the Riemannian adaptive regularization with cubics (ARC) solver indicating that the model function at the current (outer) iterate,

$$
m_k(X) = f(p_k) + ⟨X, \operatorname{grad} f(p^{(k)})⟩ + \frac{1}{2}⟨X, \operatorname{Hess} f(p^{(k)})[X]⟩ + \frac{σ_k}{3}\lVert X \rVert^3
$$

defined on the tangent space $T_{p}\mathcal M$ fulfills at the current iterate $X_k$ that

$$
m(X_k) \leq m(0)
\quad\text{ and }\quad
\lVert \operatorname{grad} m(X_k) \rVert ≤ θ \lVert X_k \rVert^2
$$

# Fields

  * `θ`:      the factor $θ$ in the second condition
  * `at_iteration::Int`: an integer indicating at which the stopping criterion last indicted to stop, which might also be before the solver started (`0`). Any negative value indicates that this was not yet the case;

# Constructor

```
StopWhenAllLanczosVectorsUsed(θ)
```

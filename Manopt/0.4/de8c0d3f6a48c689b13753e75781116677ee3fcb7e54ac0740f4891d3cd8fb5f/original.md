```
get_cost(TpM, trmo::AdaptiveRagularizationWithCubicsModelObjective, X)
```

Evaluate the tangent space [`AdaptiveRagularizationWithCubicsModelObjective`](@ref)

$$
m(X) = f(p) + ⟨\operatorname{grad} f(p), X ⟩_p + \frac{1}{2} ⟨\operatorname{Hess} f(p)[X], X⟩_p
       +  \frac{σ}{3} \lVert X \rVert^3,
$$

at `X`, cf. Eq. (33) in [AgarwalBoumalBullinsCartis:2020](@cite).

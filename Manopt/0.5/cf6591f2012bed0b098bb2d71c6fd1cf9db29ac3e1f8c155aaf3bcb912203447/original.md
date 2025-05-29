```
get_gradient(TpM, trmo::AdaptiveRagularizationWithCubicsModelObjective, X)
```

Evaluate the gradient of the [`AdaptiveRagularizationWithCubicsModelObjective`](@ref)

$$
\operatorname{grad} m(X) = \operatorname{grad} f(p) + \operatorname{Hess} f(p)[X]
       + σ\lVert X \rVert X,
$$

at `X`, cf. Eq. (37) in [AgarwalBoumalBullinsCartis:2020](@cite).

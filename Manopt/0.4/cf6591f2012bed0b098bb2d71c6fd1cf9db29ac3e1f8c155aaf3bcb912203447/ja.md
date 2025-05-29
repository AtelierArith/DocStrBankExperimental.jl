```
get_gradient(TpM, trmo::AdaptiveRagularizationWithCubicsModelObjective, X)
```

[`AdaptiveRagularizationWithCubicsModelObjective`](@ref)の勾配を評価します。

$$
\operatorname{grad} m(X) = \operatorname{grad} f(p) + \operatorname{Hess} f(p)[X]
       + σ\lVert X \rVert X,
$$

`X`において、[AgarwalBoumalBullinsCartis:2020](@cite)の式(37)を参照してください。

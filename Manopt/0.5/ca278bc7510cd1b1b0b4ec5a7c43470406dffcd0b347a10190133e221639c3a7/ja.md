```
get_gradient(TpM, trmo::TrustRegionModelObjective, X)
```

[`TrustRegionModelObjective`](@ref)の勾配を評価します。

$$
\operatorname{grad} m(X) = \operatorname{grad} f(p) + \operatorname{Hess} f(p)[X].
$$

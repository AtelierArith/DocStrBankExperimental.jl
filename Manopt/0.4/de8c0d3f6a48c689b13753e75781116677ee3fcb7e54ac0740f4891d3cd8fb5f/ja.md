```
get_cost(TpM, trmo::AdaptiveRagularizationWithCubicsModelObjective, X)
```

接触空間 [`AdaptiveRagularizationWithCubicsModelObjective`](@ref) を評価します。

$$
m(X) = f(p) + ⟨\operatorname{grad} f(p), X ⟩_p + \frac{1}{2} ⟨\operatorname{Hess} f(p)[X], X⟩_p
       +  \frac{σ}{3} \lVert X \rVert^3,
$$

`X` において、[AgarwalBoumalBullinsCartis:2020](@cite) の式 (33) を参照してください。

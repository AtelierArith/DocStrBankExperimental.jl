```
change_representer(M::GeneralizedGrassmann, ::EuclideanMetric, p, X)
```

Change `X` to the corresponding representer of a cotangent vector at `p` with respect to the scaled metric of the [`GeneralizedGrassmann`](@ref) `M`, i.e, since

$$
g_p(X,Y) = \operatorname{tr}(Y^{\mathrm{H}}BZ) = \operatorname{tr}(X^{\mathrm{H}}Z) = ⟨X,Z⟩
$$

has to hold for all $Z$, where the repreenter `X` is given, the resulting representer with respect to the metric on the [`GeneralizedGrassmann`](@ref) is given by $Y = B^{-1}X$.

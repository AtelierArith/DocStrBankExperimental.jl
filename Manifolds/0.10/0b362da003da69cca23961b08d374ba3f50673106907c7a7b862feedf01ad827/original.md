```
change_representer(M::PositiveNumbers, E::EuclideanMetric, p, X)
```

Given a tangent vector $X ∈ T_p\mathcal M$ representing a linear function with respect to the [`EuclideanMetric`](@extref `ManifoldsBase.EuclideanMetric`) `g_E`, this function changes the representer into the one with respect to the positivity metric representation of [`PositiveNumbers`](@ref) `M`.

For all tangent vectors $Y$ the result $Z$ has to fulfill

$$
    ⟨X,Y⟩ = XY = \frac{ZY}{p^2} = g_p(YZ)
$$

and hence $Z = p^2X$

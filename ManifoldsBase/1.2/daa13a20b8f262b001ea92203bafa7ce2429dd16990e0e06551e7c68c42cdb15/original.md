```
change_representer(M::AbstractManifold, G2::AbstractMetric, p, X)
```

Convert the representer `X` of a linear function (in other words a cotangent vector at `p`) in the tangent space at `p` on the [`AbstractManifold`](@ref) `M` given with respect to the [`AbstractMetric`](@ref) `G2` into the representer with respect to the (implicit) metric of `M`.

In order to convert `X` into the representer with respect to the (implicitly given) metric $g_1$ of `M`, we have to find the conversion function $c: T_p\mathcal M \to T_p\mathcal M$ such that

$$
    g_2(X,Y) = g_1(c(X),Y)
$$

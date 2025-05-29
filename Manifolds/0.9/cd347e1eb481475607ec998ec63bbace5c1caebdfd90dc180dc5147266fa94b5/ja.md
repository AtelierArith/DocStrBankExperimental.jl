```
project(M::AbstractSphere, p, X)
```

点 `X` を [`Sphere`](@ref) `M` の点 `p` における接空間に射影します。

$$
\operatorname{proj}_{p}(X) = X - \Re(⟨p, X⟩)p
$$

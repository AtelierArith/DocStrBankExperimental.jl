```
project(M::AbstractSphere, p, X)
```

Project the point `X` onto the tangent space at `p` on the [`Sphere`](@ref) `M`.

$$
\operatorname{proj}_{p}(X) = X - \Re(⟨p, X⟩)p
$$

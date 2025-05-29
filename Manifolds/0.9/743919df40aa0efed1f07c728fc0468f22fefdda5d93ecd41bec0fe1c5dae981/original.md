```
exp(M::AbstractSphere, p, X)
```

Compute the exponential map from `p` in the tangent direction `X` on the [`AbstractSphere`](@ref) `M` by following the great arc emanating from `p` in direction `X`.

$$
\exp_p X = \cos(\lVert X \rVert_p)p + \sin(\lVert X \rVert_p)\frac{X}{\lVert X \rVert_p},
$$

where $\lVert X \rVert_p$ is the [`norm`](@ref norm(::AbstractSphere,p,X)) on the tangent space at `p` of the [`AbstractSphere`](@ref) `M`.

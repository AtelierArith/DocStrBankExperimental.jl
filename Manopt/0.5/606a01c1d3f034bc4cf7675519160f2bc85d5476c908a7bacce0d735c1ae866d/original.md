```
reflect(M, f, x; kwargs...)
reflect!(M, q, f, x; kwargs...)
```

reflect the point `x` from the manifold `M` at the point `f(x)` of the function $f: \mathcal M → \mathcal M$, given by

$$
    \operatorname{refl}_f(x) = \operatorname{refl}_{f(x)}(x),
$$

Compute the result in `q`.

see also [`reflect`](@ref reflect(M::AbstractManifold, p, x))`(M,p,x)`, to which the keywords are also passed to.

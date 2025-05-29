```
log(G::AbstractLieGroup, g, h)
log(G::AbstractLieGroup, g)
log(G::AbstractLieGroup, g::Identity, T)
log!(G::AbstractLieGroup, X::T, g)
```

Compute the (Lie group) logarithmic function $\log_{\mathcal G}: \mathcal G → \mathfrak g$, which is the inverse of the [Lie group exponential function](@ref exp(::AbstractLieGroup, :Any)). For the allocating variant, you can specify the type `T`, when the point argument is the identity and hence does not provide the representation used. The computation can be performed in-place of `X::T`, which then determines the type.

!!! info "Naming convention"
    There are at least two different objects usually called “logarithm” that need to be distinguished

      * the [(Riemannian) logarithm](@extref `Base.log-Tuple{AbstractManifold, Any, Any}`) map `log(M, p, q)` from [`ManifoldsBase.jl`](https://juliamanifolds.github.io/ManifoldsBase.jl/). This can be accessed here using `log(base_manifold(G), p, q)`.
      * the logarithmic map for a (left/right/bi-invariant) Cartan-Schouten (pseudo-)metric `log(G, g, h)`, which we use as a default within this package
      * the (matrix/Lie group) logarithm function `log(G, h)` which agrees with the previous one for `g` being the identity there.


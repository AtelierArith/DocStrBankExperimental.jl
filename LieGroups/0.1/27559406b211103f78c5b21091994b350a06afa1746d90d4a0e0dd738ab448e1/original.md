```
log(G::AbstractLieGroup, g, h)
log!(G::AbstractLieGroup, X, g, h)
```

Compute the Lie group logarithmic map $\log_g: \mathcal G → \mathfrak g$, where $\mathfrak g$ denotes the [`LieAlgebra`](@ref) of $\mathcal G$. It is given by

$$
\log_g h = \log_{\mathcal G}(g^{-1}∘h)
$$

where $\log_{\mathcal G}$ denotes the [Lie group logarithmic function](@ref log(::AbstractLieGroup, :Any)) The computation can be performed in-place of `X`.

!!! info "Naming convention"
    There are at least two different objects usually called “logarithm” that need to be distinguished

      * the [(Riemannian) logarithmic map](@extref `Base.log-Tuple{AbstractManifold, Any, Any}`) `log(M, p, X)` from [`ManifoldsBase.jl`](https://juliamanifolds.github.io/ManifoldsBase.jl/)
      * the exponential map for a (left/right/bi-invariant) Cartan-Schouten (pseudo-)metric `exp(G, g, X)`, which we use as a default within this package
      * the (matrix/Lie group) exponential function `exp(G, g)` which agrees with the previous one for `g` being the identity there.


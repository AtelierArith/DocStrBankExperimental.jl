```
exp(G::AbstractLieGroup, X::T)
exp!(G::AbstractLieGroup, g, X)
```

Compute the (Lie group) exponential function

$$
\exp_{\mathcal G}: \mathfrak g → \mathcal G,\qquad \exp_{\mathcal G}(X) = γ_X(1),
$$

where $γ_X$ is the unique solution of the initial value problem

$$
γ(0) = \mathrm{e}, \quad γ'(s) = γ(s)⋅X.
$$

See also [HilgertNeeb:2012; Definition 9.2.2](@cite). On matrix Lie groups this is the same as the [matrix exponential](https://en.wikipedia.org/wiki/Matrix_exponential).

The computation can be performed in-place of `g`.

!!! info "Naming convention"
    There are at least two different objects usually called “exponential” that need to be distinguished

      * the [(Riemannian) exponential map](@extref `Base.exp-Tuple{AbstractManifold, Any, Any}`) `exp(M, p, X)` from [`ManifoldsBase.jl`](https://juliamanifolds.github.io/ManifoldsBase.jl/). This can be accessed here using `exp(base_manifold(G), p, X)`
      * the exponential map for a (left/right/bi-invariant) Cartan-Schouten (pseudo-)metric `exp(G, g, X)`, which we use as a default within this package
      * the (matrix/Lie group) exponential function `exp(G, g)` which agrees with the previous one for `g` being the identity there.


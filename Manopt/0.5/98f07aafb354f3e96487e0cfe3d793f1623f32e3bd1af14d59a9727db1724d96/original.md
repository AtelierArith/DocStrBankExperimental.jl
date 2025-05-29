```
reflect(M, p, x, kwargs...)
reflect!(M, q, p, x, kwargs...)
```

Reflect the point `x` from the manifold `M` at point `p`, given by

$$
\operatorname{refl}_p(q) = \operatorname{retr}_p(-\operatorname{retr}^{-1}_p q),
$$

where $\operatorname{retr}$ and $\operatorname{retr}^{-1}$ denote a retraction and an inverse retraction, respectively.

This can also be done in place of `q`.

## Keyword arguments

  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: a retraction $\operatorname{retr}$ to use, see [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: an inverse retraction $\operatorname{retr}^{-1}$ to use, see [the section on retractions and their inverses](@extref ManifoldsBase :doc:`retractions`)

and for the `reflect!` additionally

  * `X=zero_vector(M,p)`: a temporary memory to compute the inverse retraction in place. otherwise this is the memory that would be allocated anyways.

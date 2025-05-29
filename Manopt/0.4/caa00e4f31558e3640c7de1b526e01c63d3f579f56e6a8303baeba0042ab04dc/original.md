```
reflect(M, p, x, kwargs...)
reflect!(M, q, p, x, kwargs...)
```

Reflect the point `x` from the manifold `M` at point `p`, given by

$$
    \operatorname{refl}_p(x) = \operatorname{retr}_p(-\operatorname{retr}^{-1}_p x).
$$

where $\operatorname{retr}$ and $\operatorname{retr}^{-1}$ denote a retraction and an inverse retraction, respectively. This can also be done in place of `q`.

## Keyword arguments

  * `retraction_method`:         (`default_retraction_metiod(M, typeof(p))`) the retraction to use in the reflection
  * `inverse_retraction_method`: (`default_inverse_retraction_method(M, typeof(p))`) the inverse retraction to use within the reflection

and for the `reflect!` additionally

  * `X`:                         (`zero_vector(M,p)`) a temporary memory to compute the inverse retraction in place. otherwise this is the memory that would be allocated anyways.

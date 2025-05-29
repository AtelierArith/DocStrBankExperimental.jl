```julia
domain_kind(x)

```

Return the *kind* of a domain type (preferred) or value. Errors for objects/types which are not domains. Also works for domains of transformations.

The following return values are possible:

1. `:univariate`, the bounds of which can be accessed using `minimum`, `maximum`, and

`extrema`,

2. `:multivariate`, which supports `length`, `getindex` (`[]`), and conversion with `Tuple`.

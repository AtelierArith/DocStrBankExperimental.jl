```
ordered(d::Distribution)
```

Return a `Distribution` whose support are ordered vectors, i.e., vectors with increasingly ordered elements.

Specifically, `d` is restricted to the subspace of its domain containing only ordered elements.

!!! warning
    `rand` is implemented using rejection sampling, which can be slow for high-dimensional distributions. In such cases, consider using MCMC methods to sample from the distribution instead.


!!! warning
    The resulting ordered distribution is un-normalized, which can cause issues in some contexts, e.g. in hierarchical models where the parameters of the ordered distribution are themselves sampled. See the notes below for a more detailed discussion.


## Notes on `ordered` being un-normalized

The resulting ordered distribution is un-normalized. This is not a problem if used in a context where the normalizing factor is irrelevant, but if the value of the normalizing factor impacts the resulting computation, the results may be inaccurate.

For example, if the distribution is used in sampling a posterior distribution with MCMC and the parameters of the ordered distribution are themselves sampled, then the normalizing factor would in general be needed for accurate sampling, and `ordered` should not be used. However, if the parameters are fixed, then since MCMC does not require distributions be normalized, `ordered` may be used without problems.

A common case is where the distribution being ordered is a joint distribution of `n` identical univariate distributions. In this case the normalization factor works out to be the constant `n!`, and `ordered` can again be used without problems even if the parameters of the univariate distribution are sampled.

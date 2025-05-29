```
logpdf(lfgp::LatentFiniteGP, y::NamedTuple{(:f, :y)})
```

$$
    log p(y, f; x)
$$

The joint log density of the Gaussian process output `f` and observation `y`.

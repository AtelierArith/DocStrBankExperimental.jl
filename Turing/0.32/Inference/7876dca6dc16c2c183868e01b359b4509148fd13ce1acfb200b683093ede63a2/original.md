```
MH(space...)
```

Construct a Metropolis-Hastings algorithm.

The arguments `space` can be

  * Blank (i.e. `MH()`), in which case `MH` defaults to using the prior for each parameter as the proposal distribution.
  * A set of one or more symbols to sample with `MH` in conjunction with `Gibbs`, i.e. `Gibbs(MH(:m), PG(10, :s))`
  * An iterable of pairs or tuples mapping a `Symbol` to a `AdvancedMH.Proposal`, `Distribution`, or `Function` that generates returns a conditional proposal distribution.
  * A covariance matrix to use as for mean-zero multivariate normal proposals.

# Examples

The default `MH` will use propose samples from the prior distribution using `AdvancedMH.StaticProposal`.

```julia
@model function gdemo(x, y)
    s² ~ InverseGamma(2,3)
    m ~ Normal(0, sqrt(s²))
    x ~ Normal(m, sqrt(s²))
    y ~ Normal(m, sqrt(s²))
end

chain = sample(gdemo(1.5, 2.0), MH(), 1_000)
mean(chain)
```

Alternatively, you can specify particular parameters to sample if you want to combine sampling from multiple samplers:

```julia
@model function gdemo(x, y)
    s² ~ InverseGamma(2,3)
    m ~ Normal(0, sqrt(s²))
    x ~ Normal(m, sqrt(s²))
    y ~ Normal(m, sqrt(s²))
end

# Samples s with MH and m with PG
chain = sample(gdemo(1.5, 2.0), Gibbs(MH(:s), PG(10, :m)), 1_000)
mean(chain)
```

Using custom distributions defaults to using static MH:

```julia
@model function gdemo(x, y)
    s² ~ InverseGamma(2,3)
    m ~ Normal(0, sqrt(s²))
    x ~ Normal(m, sqrt(s²))
    y ~ Normal(m, sqrt(s²))
end

# Use a static proposal for s and random walk with proposal
# standard deviation of 0.25 for m.
chain = sample(
    gdemo(1.5, 2.0),
    MH(
        :s => InverseGamma(2, 3),
        :m => Normal(0, 1)
    ),
    1_000
)
mean(chain)
```

Specifying explicit proposals using the `AdvancedMH` interface:

```julia
@model function gdemo(x, y)
    s² ~ InverseGamma(2,3)
    m ~ Normal(0, sqrt(s²))
    x ~ Normal(m, sqrt(s²))
    y ~ Normal(m, sqrt(s²))
end

# Use a static proposal for s and random walk with proposal
# standard deviation of 0.25 for m.
chain = sample(
    gdemo(1.5, 2.0),
    MH(
        :s => AdvancedMH.StaticProposal(InverseGamma(2,3)),
        :m => AdvancedMH.RandomWalkProposal(Normal(0, 0.25))
    ),
    1_000
)
mean(chain)
```

Using a custom function to specify a conditional distribution:

```julia
@model function gdemo(x, y)
    s² ~ InverseGamma(2,3)
    m ~ Normal(0, sqrt(s²))
    x ~ Normal(m, sqrt(s²))
    y ~ Normal(m, sqrt(s²))
end

# Use a static proposal for s and and a conditional proposal for m,
# where the proposal is centered around the current sample.
chain = sample(
    gdemo(1.5, 2.0),
    MH(
        :s => InverseGamma(2, 3),
        :m => x -> Normal(x, 1)
    ),
    1_000
)
mean(chain)
```

Providing a covariance matrix will cause `MH` to perform random-walk sampling in the transformed space with proposals drawn from a multivariate normal distribution. The provided matrix must be positive semi-definite and square. Usage:

```julia
@model function gdemo(x, y)
    s² ~ InverseGamma(2,3)
    m ~ Normal(0, sqrt(s²))
    x ~ Normal(m, sqrt(s²))
    y ~ Normal(m, sqrt(s²))
end

# Providing a custom variance-covariance matrix
chain = sample(
    gdemo(1.5, 2.0),
    MH(
        [0.25 0.05;
         0.05 0.50]
    ),
    1_000
)
mean(chain)
```

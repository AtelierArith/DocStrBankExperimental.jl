```
HeterogeneousMixture(distributions::Vector{Distribution{T}}) where {T}
```

Define a new distribution that is a mixture of a given list of base distributions.

The argument is the vector of base distributions, one for each mixture component.

Note that the base distributions must have the same output type.

Example:

```julia
uniform_beta_mixture = HeterogeneousMixture([uniform, beta])
```

The resulting mixture distribution takes `n+1` arguments, where `n` is the sum of the number of arguments taken by each distribution in the list. The first argument to the mixture distribution is a vector of non-negative mixture weights, which must sum to 1.0. The remaining arguments are the arguments to each mixture component distribution, in order in which the distributions are passed into the constructor.

Example:

```julia
@gen function foo()
    # mixure of a uniform distribution on the interval [`lower`, `upper`]
    # and a beta distribution with alpha parameter `a` and beta parameter `b`
    # the uniform as weight 0.4 and the beta has weight 0.6
    x ~ uniform_beta_mixture([0.4, 0.6], lower, upper, a, b)
end
```

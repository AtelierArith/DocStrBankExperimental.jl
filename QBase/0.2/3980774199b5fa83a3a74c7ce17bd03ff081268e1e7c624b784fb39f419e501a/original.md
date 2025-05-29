```
outcome_probabilities(
    conditionals::ConditionalDistribution,
    priors :: ProbabilityDistribution;
    atol=ATOL :: Float64
) :: ProbabilityDistribution
```

Returns the probability of each outcome given priors and conditional probabilities. For convenience, this method can be called with an abstract vector/matrix

```
outcome_probabilities(
    conditionals :: AbstractMatrix{<:Real},
    priors :: AbstractVector{<:Real};
    atol=ATOL :: Float64
)
```

Furthermore, the ordering of the arguments can be reversed. A `DomainError` is thrown if the constructed vector is not a valid probability distribution.

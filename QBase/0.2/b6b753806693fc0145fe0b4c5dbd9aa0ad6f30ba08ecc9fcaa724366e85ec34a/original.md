```
JointProbabilities(
    distribution :: Matrix{<:Real};
    atol=ATOL :: Float64
) <: JointProbabilityDistribution
```

A struct representing a discrete probability distribution. All elements in the marginal distribution must be positive and their sum must be one. For convenience, the `JointProbabilities` can also be constructed by passing in a `ConditionalDistribution` and a `ProbabilityDistribution`,

```
JointProbabilities(
    priors :: AbstractVector{<:Real},
    conditionals :: AbstractMatrix{<:Real};
    atol=ATOL :: Float64
)
```

Or, two `ProbabilityDistribution`s can be provided

```
JointProbabilities(
    priors1 :: AbstractVector{<:Real},
    priors2 :: AbstractVector{<:Real};
    atol=ATOL :: Float64
)
```

A `DomainError` is thrown if the joint probability distribution is invalid.

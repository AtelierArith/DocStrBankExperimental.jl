```julia
AltMultinomial(total_count, partial_probabilities)

```

Multinomial distribution for the given `total_count`. The last probability should not be specified, as it is calculated as a residual. Small numerical error is tolerated, negative probabilities are not.

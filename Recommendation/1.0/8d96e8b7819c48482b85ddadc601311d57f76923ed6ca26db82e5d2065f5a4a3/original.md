```
IntraListSimilarity
```

Sum of similarities between every pairs of recommended items. Larger value represents less diversity.

  * Reference: [Improving Recommendation Lists Through Topic Diversification](http://files.grouplens.org/papers/ziegler-www05.pdf)

```julia
measure(
    metric::IntraListSimilarity, recommendations::Union{AbstractSet, AbstractVector};
    sims::AbstractMatrix
)
```

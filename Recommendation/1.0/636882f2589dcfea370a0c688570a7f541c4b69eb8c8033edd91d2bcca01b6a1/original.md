```
get_pairwise_preference_triples(R::AbstractMatrix) -> Vector{Tuple{Int, Int, Int}}
```

Return user-item-item triples corresponding to a user-item matrix `R` (i.e., $(u, i, j) \in D_s$ in [BPR: Bayesian Personalized Ranking from Implicit Feedback](https://dl.acm.org/doi/10.5555/1795114.1795167)). In the pairwise item ranking context, each triple represents that user $u$ prefers item $i$ over $j$.

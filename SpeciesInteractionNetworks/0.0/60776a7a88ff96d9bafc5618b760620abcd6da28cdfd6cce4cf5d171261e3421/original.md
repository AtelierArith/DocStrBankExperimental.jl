```
links_variance(N::SpeciesInteractionNetwork{<:Partiteness, <:Probabilistic})
```

The variance in the expected number of links in a probabilistic network is defined as the sum of $p \times (1 - p)$, where $p$ is the probability of all interactions (including $p = 0$).

###### References

[Poisot2015structure](@citet*)

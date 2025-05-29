```
hitting_location_distribution(tpt)
```

Compute the distribution of target-hitting locations. 

Return a matrix `R` such that `R[i, j]` is the probability that - starting in state `i` - the first visit to `B` occurs in state `j`. Note that  `R[i, j] == 0` for all `j ∉ B`.

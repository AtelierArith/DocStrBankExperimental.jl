```
FD_obs_metrics(trait_matrix::Trait_Matrix, weight)
```

Compute observation-based metrics of functional diversity: Originality, Uniqueness, and Contribution.

# Arguments

  * `trait_matrix::Trait_Matrix`: A trait matrix containing trait values for different species.
  * `weight`: Vector of weight parameters for each traits in the trait matrix. Can be missing, in this case, each traits are consider equals.

# Returns

  * `Obs_metrics`: DataFrame containing observation-based metrics for each species.

# Details

The function calculates three observation-based metrics of functional diversity:

1. Species Contribution: Contribution of each species to the overall functional richness.
2. Species Originality: Average distance of each species to all other species in trait space.
3. Species Uniqueness: Minimum distance of each species to any other species in trait space.

The contribution of each species is calculated by iteratively removing one species at a time, recalculating the functional richness, and computing the difference from the total richness.  Originality is calculated as the average distance of each species to all other species, while uniqueness is calculated as the minimum distance of each species to any other species.

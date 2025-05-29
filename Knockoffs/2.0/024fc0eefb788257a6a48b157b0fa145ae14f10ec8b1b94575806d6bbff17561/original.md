```
choose_group_reps(Σ::Symmetric, groups::AbstractVector; [threshold=0.5], [prioritize_idx], [Σinv])
```

Chooses group representatives. Returns indices of `Σ` that are representatives. If R is the set of selected variables within a group and O is the set of variables outside the group, then we keep adding variables to R until the proportion of variance explained by R divided by the proportion of variance explained by R and O exceeds `threshold`. 

# Inputs

  * `Σ`: Correlation matrix wrapped in the `Symmetric` argument.
  * `groups`: Vector of group membership.

# Optional inputs

  * `threshold`: Value between 0 and 1 that controls the number of    representatives per group. Larger means more representatives (default 0.5)
  * `prioritize_idx`: Variable indices that should receive priority to be chosen   as representatives, defaults to `nothing`
  * `Σinv`: Precomputed `inv(Σ)` (it will be computed if not supplied)

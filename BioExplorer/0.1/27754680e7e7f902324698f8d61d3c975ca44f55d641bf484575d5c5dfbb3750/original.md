```
matrix_Gowdis(trait_matrix::Trait_Matrix, weight)
```

Compute the Gower distance between every pair of species within a trait matrix.

# Arguments

  * `trait_matrix::Trait_Matrix`: A trait matrix containing species trait data.
  * `weight`: Vector of weight parameters for each traits in the trait matrix. Can be missing, in this case, each traits are consider equals.

# Returns

  * A matrix representing the Gower distance between every pair of species.

# Details

The function computes the Gower distance between every pair of species based on their trait data within the given trait matrix. It iterates over all combinations of species and computes the pairwise Gower distance using the `pairwise_Gowdis` function. The resulting matrix represents the Gower distance between every pair of species.

See also [`pairwise_Gowdis`](@ref)

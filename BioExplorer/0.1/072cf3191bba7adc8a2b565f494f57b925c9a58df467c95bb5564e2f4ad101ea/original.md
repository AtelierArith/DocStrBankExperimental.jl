```
pairwise_Gowdis(trait_matrix::Trait_Matrix, weight, species1::String, species2::String)
```

Compute the Gower distance between a pair of species within a trait matrix.

# Arguments

  * `trait_matrix::Trait_Matrix`: A trait matrix containing species trait data.
  * `weight`: Vector of weight parameters for each traits in the trait matrix. Can be missing, in this case, each traits are consider equals.
  * `species1::String`: The name of the first species.
  * `species2::String`: The name of the second species.

# Returns

  * The Gower distance between the two species.

# Details

The function computes the Gower distance between a pair of species based on their trait data within the given trait matrix.  Gower distance is a measure of dissimilarity that accounts for different types of variables (categorical, numerical, and ordinal) and their respective weights. The dissimilarity is calculated for each trait variable and then combined using the provided weights to obtain the final Gower distance.

See also [`matrix_Gowdis`](@ref)

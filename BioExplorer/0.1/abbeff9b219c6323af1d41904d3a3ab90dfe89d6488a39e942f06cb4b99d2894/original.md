```
jaccard_dissim_matrix(community_matrix::Community_Matrix)
```

Compute the Jaccard dissimilarity matrix between all communities in a community matrix.

# Arguments

  * `community_matrix::Community_Matrix`: A community matrix containing species data for multiple communities.

# Returns

  * `beta_matrix::DataFrame`: A DataFrame representing the Jaccard dissimilarity matrix between all pairs of communities.

# Details

The function calculates the Jaccard dissimilarity between all pairs of communities in the given community matrix.  It iterates over all possible combinations of communities and computes the Jaccard dissimilarity using the `jaccard_dissim` function.  The result is stored in a DataFrame where each row and column represent a community, and the values represent the Jaccard dissimilarity between corresponding pairs of communities.

See also [`jaccard_dissim`](@ref)

```
jaccard_dissim(community_matrix::Community_Matrix)
```

Compute the Jaccard dissimilarity between two communities.

# Arguments

  * `community_matrix::Community_Matrix`: A community matrix containing species data for two communities. If more than communities are present, only the two first ones are considered.

# Returns

  * `jaccard_dissim_value::Float64`: The Jaccard dissimilarity value between the two communities.

# Details

The Jaccard dissimilarity measures dissimilarity between two sets by comparing their intersection to their union.  For two communities represented by binary species presence-absence data, it is calculated as the number of species found in only one of the communities divided by the total number of species found in either community.

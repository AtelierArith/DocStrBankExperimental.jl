```
rank(community_matrix::Community_Matrix, community_selected::String)
```

Rank the species according to their abundance in a selected community.

# Arguments

  * `community_matrix::Community_Matrix`: The input community matrix.
  * `community_selected::String`: The name of the community for which species ranking is required.

# Returns

A tuple `(community_name, community_ranked)` where:

  * `community_name` is the name of the selected community.
  * `community_ranked` is a DataFrame containing species ranked by abundance in the selected community.

# Details

This function ranks the species according to their abundance in the specified community of the input community matrix.  It sorts the species by abundance in descending order and assigns ranks.  If species have the same abundance, they are assigned the same rank (ex-aequo ranking).  The function removes species with zero abundance.

See also [`whittacker_plot`](@ref)

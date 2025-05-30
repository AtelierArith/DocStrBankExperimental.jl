```
beta_carvalho_matrix(community_matrix::Community_Matrix)
```

Compute the beta diversity matrix between all pairs of communities in a community matrix according to the Carvalho framework: Carvalho, J. C., Cardoso, P., Borges, P. A. V., Schmera, D., & Podani, J. (2013). Measuring fractions of beta diversity and their relationships to nestedness: A theoretical and empirical comparison of novel approaches. Oikos, 122(6), 825-834. https://doi.org/10.1111/j.1600-0706.2012.20980.x

# Arguments

  * `community_matrix::Community_Matrix`: A community matrix containing species data for multiple communities.

# Returns

  * An array containing three DataFrames representing the beta diversity matrices for total dissimilarity, replacement dissimilarity, and richness dissimilarity.

# Details

The function calculates beta diversity between all pairs of communities using the Carvalho framework, which decomposes beta diversity into three components: total dissimilarity, replacement dissimilarity, and richness dissimilarity.  For each component, a separate DataFrame is returned where each row and column represent a community, and the values represent the beta diversity between corresponding pairs of communities.

See also [`beta_carvalho`](@ref)

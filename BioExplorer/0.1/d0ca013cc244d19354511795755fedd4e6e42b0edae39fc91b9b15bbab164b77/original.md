```
beta_carvalho(community_matrix::Community_Matrix)
```

Compute beta diversity between two communities of a community matrix according to the Carvalho framework:

# Arguments

  * `community_matrix::Community_Matrix`: A community matrix containing species data for two communities. If more than communities are present, only the two first ones are considered.

# Returns

  * An array containing three components of beta diversity: total dissimilarity, replacement dissimilarity, and richness dissimilarity.

# Details

The function calculates beta diversity between two communities using the Carvalho framework, which decomposes beta diversity into three components: total dissimilarity, replacement dissimilarity, and richness dissimilarity.  Total dissimilarity measures the overall difference in species composition between two communities.  Replacement dissimilarity measures the extent to which species in one community are replaced by different species in the other community.  Richness dissimilarity measures the difference in species richness between the two communities.

# Reference

Carvalho, J. C., Cardoso, P., Borges, P. A. V., Schmera, D., & Podani, J. (2013). Measuring fractions of beta diversity and their relationships to nestedness: A theoretical and empirical comparison of novel approaches. Oikos, 122(6), 825-834. https://doi.org/10.1111/j.1600-0706.2012.20980.x

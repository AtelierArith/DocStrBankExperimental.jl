```
hill(community_matrix::Community_Matrix)
```

Compute the Hill series for all communities within a community matrix.

# Arguments

  * `community_matrix::Community_Matrix`: A community matrix containing species abundance data for multiple communities.

# Returns

  * A DataFrame representing the Hill series for each community, including Hill numbers H0, H1, H2, and H3.

# Details

The function calculates the Hill series, which represents the equivalent number of species at different orders of Hill number, for each community within the given community matrix.  Hill numbers measure biodiversity by scaling species abundance to a common unit, providing a way to compare biodiversity across different communities.  The output DataFrame contains the Hill numbers H0, H1, H2, and H3 for each community.

# Reference

Hill, M. O. (1973). Diversity and Evenness: A Unifying Notation and Its Consequences. Ecology, 54(2), 427–432. https://doi.org/10.2307/1934352

```
pielou_evenness(community_matrix::Community_Matrix)
```

Compute an evenness diversity metric according to the Pielou's framework.

# Arguments

  * `community_matrix::Community_Matrix`: A community matrix containing species abundance data.

# Returns

  * A DataFrame containing the Pielou's evenness (J) metric for each community.

# Details

The function calculates the Pielou's evenness (J) metric for each community within the given community matrix.  Pielou's evenness measures the equitability of species abundance distribution within a community.  It is calculated as the Shannon-Wiener entropy divided by the maximum possible entropy, which is the logarithm of the species richness. 

# Reference

Pielou, E. C. (1969). An Introduction to Mathematical Ecology. Wiley-Interscience.

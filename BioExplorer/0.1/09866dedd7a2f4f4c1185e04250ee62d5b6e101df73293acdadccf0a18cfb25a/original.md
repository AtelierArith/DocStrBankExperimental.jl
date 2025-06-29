```
sampling_coverage(community_matrix::Community_Matrix)
```

Compute the percentage of sampling coverage according to the Chao framework.

# Arguments

  * `community_matrix::Community_Matrix`: A community matrix containing species abundance data.

# Returns

  * The percentage of sampling coverage.

# Details

The function calculates the percentage of sampling coverage, which estimates the proportion of total species in the community that have been sampled.  It uses the Chao framework, which considers the abundance of rare species to estimate the coverage. The output represents the percentage of species that have been sampled based on the observed data.

# Reference

Chao, A., Kubota, Y., Zelený, D., Chiu, C., Li, C., Kusumoto, B., Yasuhara, M., Thorn, S., Wei, C., Costello, M. J., & Colwell, R. K. (2020). Quantifying sample completeness and comparing diversities among assemblages. Ecological Research, 35(2), 292–314. https://doi.org/10.1111/1440-1703.12102

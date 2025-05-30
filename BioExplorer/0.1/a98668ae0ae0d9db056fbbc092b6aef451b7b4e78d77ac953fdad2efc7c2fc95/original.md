biodiversity*estimate(community*matrix::Community_Matrix)

Compute several estimations of the number of species in a community.

# Arguments

  * `community_matrix::Community_Matrix`: The input community matrix.

# Returns

  * A DataFrame containing the estimators and their corresponding values.

# Details

This function computes several estimations of the number of species in a community based on incidence or abundance data.  It calculates the Jackknife1, Jackknife2, Chao1, and Chao2 estimators of species richness.

See also [`sampling_coverage`](@ref)

# Reference

Chao, A., Chiu, C.-H., & Jost, L. (2014). Unifying Species Diversity, Phylogenetic Diversity, Functional Diversity, and Related Similarity and Differentiation Measures Through Hill Numbers. Annual Review of Ecology, Evolution, and Systematics, 45(1), 297–324. https://doi.org/10.1146/annurev-ecolsys-120213-091540

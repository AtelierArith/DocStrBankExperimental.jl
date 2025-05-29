Algorithm that calculates the cross-correlation between the source and the template.

This method computes the similarity between the source and template by multiplying their corresponding elements and summing up the results. This approach inherently favors the brighter regions of the source image over the darker ones since the product of higher intensity values will naturally be greater. Higher values indicate a better match.

# Formula

$R_i = \sum_j (S_{i+j} \cdot T_j)$

See also [`NormalizedCrossCorrelation`](@ref)

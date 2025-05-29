Normalized algorithm for computing the cross-correlation between the source and the template.

This method improves upon the [`CrossCorrelation`](@ref) by normalizing the results. It calculates the similarity by multiplying corresponding elements, summing up those products, and then dividing by the product of their norms. This reduces the bias toward brighter areas, providing a more balanced measurement of similarity. Higher values indicate a better match.

# Formula

$R_i = \frac{\sum_j (S_{i+j} \cdot T_j)}{\sqrt{\sum_j S_{i+j}^2 \cdot \sum_j T_j^2}}$

See also [`CrossCorrelation`](@ref)

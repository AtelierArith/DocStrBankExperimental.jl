Algorithm that measures the correlation coefficient between the source and the template.

This method quantifies the degree to which the source and template match by computing their correlation coefficient. It offers a balance between capturing the structural similarity and adjusting for brightness variations, making it less biased towards the brighter parts in comparison to simple cross-correlation methods. A higher value indicates a better match.

# Formula

$R_i = \frac{     \sum_j ((S_{i+j} - \bar{S}_i) \cdot (T_j - \bar{T})) }{     \sqrt{\sum_j (S_{i+j} - \bar{S}_i)^2 \cdot \sum_j (T_j - \bar{T})^2} }$

Where $\bar{S}_i$ is the mean of the source values within the region considered for matching and $\bar{T}$ is the mean of the template values.

See also [`NormalizedCorrelationCoeff`](@ref)

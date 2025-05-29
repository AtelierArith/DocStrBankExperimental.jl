Normalized algorithm for computing the correlation coefficient between the source and the template.

This method extends the [`CorrelationCoeff`](@ref) by applying additional normalization steps, aiming to further minimize the influence of the absolute brightness levels and enhance the robustness of matching. It calculates the normalized correlation coefficient, providing a standardized measure. A higher value indicates a better match.

# Formula

$R_i = \frac{     \sum_j ((S_{i+j} - \bar{S}_i) \cdot (T_j - \bar{T})) }{     \sqrt{\sum_j (S_{i+j} - \bar{S}_i)^2} \cdot \sqrt{\sum_j (T_j - \bar{T})^2} }$

Where $\bar{S}_i$ is the mean of the source values within the region considered for matching and $\bar{T}$ is the mean of the template values.

See also [`CorrelationCoeff`](@ref)

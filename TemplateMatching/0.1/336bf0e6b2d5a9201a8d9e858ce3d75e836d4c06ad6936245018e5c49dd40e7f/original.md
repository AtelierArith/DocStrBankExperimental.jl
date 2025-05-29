Normalized algorithm for computing the squared difference between the source and the template.

This method extends the [`SquareDiff`](@ref) algorithm by normalizing the squared differences. It is more robust against variations in brightness and contrast between the source and template images. Lower values indicate a better match.

# Formula

$R_i = \frac{\sum_j (S_{i+j} - T_j)^2}{\sqrt{\sum_j S_{i+j}^2 \cdot \sum_j T_j^2}}$

See also [`SquareDiff`](@ref)

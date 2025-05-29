Algorithm that calculate the squared difference between the source and the template.

This method is used to find how much each part of the source array differs from the template by squaring the difference between corresponding values. It is straightforward and works well when the brightness of the images does not vary much. Lower values indicate a better match.

# Formula

$R_i = \sum_j (S_{i+j} - T_j)^2$

See also [`NormalizedSquareDiff`](@ref)

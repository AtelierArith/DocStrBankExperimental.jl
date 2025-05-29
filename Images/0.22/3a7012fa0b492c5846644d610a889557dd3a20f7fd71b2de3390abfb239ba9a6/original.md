`findlocalmaxima(img, [region, edges]) -> Vector{CartesianIndex}`

Returns the coordinates of elements whose value is larger than all of their immediate neighbors.  `region` is a list of dimensions to consider.  `edges` is a boolean specifying whether to include the first and last elements of each dimension, or a tuple-of-Bool specifying edge behavior for each dimension separately.

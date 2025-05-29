```
match_template(source, template, alg::Algorithm)
```

Performs template matching between the source image and template using a specified algorithm.

Compare a template to a source image using the algorithm specified by the `alg` parameter. It is designed to work with arrays of more than two dimensions, making it suitable for multidimensional arrays or sets of images. The function slides the template over the source array in all possible positions, computing a similarity metric at each position.

# Arguments

  * `source`: Source array to search within.
  * `template`: Template array to search for.
  * `alg::Algorithm`: Algorithm to use for calculating the similarity metric.

The dimensions of the `source` array should be greater than or equal to the dimensions of the `template` array. If the `source` is of size `(S_1, S_2, ...)` and `template` is `(T_1, T_2, ...)`, then the size of the resultant match array will be `(S_1-T_1+1, S_2-T_2+1, ...)`, representing the similarity metric for each possible position of the template over the source.

The algorithm for matching is chosen by passing an instance of one of the following structs as the `alg` parameter: [`SquareDiff`](@ref), [`NormalizedSquareDiff`](@ref), [`CrossCorrelation`](@ref), [`NormalizedCrossCorrelation`](@ref), [`CorrelationCoeff`](@ref), or [`NormalizedCorrelationCoeff`](@ref).

# Returns

Return an array of the same number of dimensions as the input arrays, containing the calculated similarity metric at each position of the template over the source image.

# Examples

```julia
source = rand(100, 100)
template = rand(10, 10)
result = match_template(source, template, CrossCorrelation())
```

```jldoctest
source = rand(100, 100)
template = source[10:15, 20:30]
result = match_template(source, template, SquareDiff())
argmin(result)

# output
CartesianIndex(10, 20)
```

```jldoctest
source = rand(100, 100)
template = source[10:15, 20:30]
result = match_template(source, template, CorrelationCoeff())
argmax(result)

# output
CartesianIndex(10, 20)
```

See also [`match_template!`](@ref) for a version of this function that writes the result into a preallocated array.

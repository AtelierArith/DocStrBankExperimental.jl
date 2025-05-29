```
match_template!(dest, source, template, alg::Algorithm)
```

Performs template matching and writes the results into a preallocated destination array.

Inplace counterpart to `match_template`, designed to perform the template matching operation and store the results in a preallocated array `dest` passed by the user. This reduces memory allocations and can be more efficient when performing multiple template matching operations. It compares a template to a source image using the specified algorithm, suitable for multidimensional arrays or sets of images.

See [`match_template`](@ref) for further documentation.

# Arguments

  * `dest`: Preallocated destination array where the result will be stored.
  * `source`: Source array to search within.
  * `template`: Template array to search for.
  * `alg::Algorithm`: Algorithm for calculating the similarity.

# Returns

Return its first argument `dest` containing the calculated similarity metric at each position of the template over the source image.

The dimensions of the `source` array should be greater than or equal to the dimensions of the template array. If the source is of size `(S_1, S_2, ...)` and `template` is `(T_1, T_2, ...)`, then `dest` must be preallocated with dimensions `(S_1-T_1+1, S_2-T_2+1, ...)`, representing the similarity metric for each possible position of the template over the source.

The algorithm for matching is chosen by passing an instance of one of the following structs as the `alg` parameter: [`SquareDiff`](@ref), [`NormalizedSquareDiff`](@ref), [`CrossCorrelation`](@ref), [`NormalizedCrossCorrelation`](@ref), [`CorrelationCoeff`](@ref), or [`NormalizedCorrelationCoeff`](@ref).

# Examples

```julia
source = rand(100, 100)
template = rand(10, 10)
dest = Array{Float64}(undef, 91, 91)
match_template!(dest, source, template, CrossCorrelation())

dest = Array{Float64}(undef, 100, 100)
match_template!(dest, source, template, CrossCorrelation()) # will fail
```

See also [`match_template`](@ref) for an immutable version of this function.

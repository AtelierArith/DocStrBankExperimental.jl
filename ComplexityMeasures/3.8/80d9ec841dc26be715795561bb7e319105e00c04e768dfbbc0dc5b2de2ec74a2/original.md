```
SpatialBubbleSortSwaps <: SpatialOutcomeSpace
SpatialBubbleSortSwaps(stencil, x; periodic = true)
```

`SpatialBubbleSortSwaps` generalizes [`BubbleSortSwaps`](@ref) to high-dimensional arrays by encoding pixel/voxel/hypervoxel windows in terms of how many swap  operations the bubble sort algorithm requires to sort them.

What does this mean? For [`BubbleSortSwaps`](@ref) the input data is embedded using embedding dimension `m` and the number of swaps required are computed for each embedding vector. For  `SpatialBubbleSortSwaps`, the "embedding dimension" `m` for  is inferred from the number of elements in the `stencil`, and the "embedding vectors" are the  hypervoxels selected by the `stencil`. 

## Outcome space

The outcome space `Ω` for `SpatialBubbleSortSwaps` is the range of integers  `0:(n*(n-1)÷2)`, corresponding to the number of swaps required by the bubble sort algorithm to sort a particular pixel/voxel/hypervoxel window.

## Arguments

  * `stencil`. Defines what local area (hyperrectangle), or which points within this area,   to include around each hypervoxel (i.e. pixel in 2D). See    [`SpatialOrdinalPatterns`](@ref) and [`SpatialDispersion`](@ref) for   more information about stencils and examples of how to specify them.
  * `x::AbstractArray`. The input data. Must be provided because we need to know its size   for optimization and bound checking.

## Keyword arguments

  * `periodic::Bool`. If `periodic == true`, then the stencil should wrap around at the   end of the array. If `periodic = false`, then pixels whose stencil exceeds the array   bounds are skipped.

## Example

```julia
using ComplexityMeasures
using Random; rng = MersenneTwister(1234)

x = rand(rng, 100, 100, 100) # some 3D image
stencil = zeros(Int,2,2,2) # 3D stencil
stencil[:, :, 1] = [1 0; 1 1]
stencil[:, :, 2] = [0 1; 1 0]
o = SpatialBubbleSortSwaps(stencil, x)

# Distribution of "bubble sorting complexity" among voxel windows
counts_and_outcomes(o, x)

# "Spatial bubble Kaniadakis entropy", with shrinkage-adjusted probabilities
information(Kaniadakis(), Shrinkage(), o, x)
```

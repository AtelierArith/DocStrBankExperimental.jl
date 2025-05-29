```
TopNFeatures(n)
```

Select top-n features.

For outputs of convolutional layers, the relevance is summed across height and width channels for each feature.

See also [`IndexedFeatures`](@ref).

## Note

The XAIBase interface currently assumes that features have either 2 or 4 dimensions (`(features, batchsize)` or `(width, height, features, batchsize)`).

It also assumes that the batch dimension is the last dimension of the feature.

## Example

```julia-repl
julia> feature_selector = TopNFeatures(2)
 TopNFeatures(2)

julia> feature = rand(3, 2)
3×2 Matrix{Float64}:
 0.265312  0.953689
 0.674377  0.172154
 0.649722  0.570809

julia> feature_selector(feature)
2-element Vector{Vector{CartesianIndices{2, Tuple{UnitRange{Int64}, UnitRange{Int64}}}}}:
 [CartesianIndices((2:2, 1:1)), CartesianIndices((1:1, 2:2))]
 [CartesianIndices((3:3, 1:1)), CartesianIndices((3:3, 2:2))]

julia> feature = rand(3, 3, 3, 2);

julia> feature_selector(feature)
2-element Vector{Vector{CartesianIndices{4, NTuple{4, UnitRange{Int64}}}}}:
 [CartesianIndices((1:3, 1:3, 2:2, 1:1)), CartesianIndices((1:3, 1:3, 1:1, 2:2))]
 [CartesianIndices((1:3, 1:3, 1:1, 1:1)), CartesianIndices((1:3, 1:3, 3:3, 2:2))]
```

```
IndexedFeatures(indices...)
```

Select features by indices.

For outputs of convolutional layers, the index refers to a feature dimension.

See also See also [`TopNFeatures`](@ref).

## Note

The XAIBase interface currently assumes that features have either 2 or 4 dimensions (`(features, batchsize)` or `(width, height, features, batchsize)`).

It also assumes that the batch dimension is the last dimension of the feature.

## Example

```julia-repl
julia> feature_selector = IndexedFeatures(2, 3)
 IndexedFeatures(2, 3)

julia> feature = rand(3, 3, 3, 2);

julia> feature_selector(feature)
2-element Vector{Vector{CartesianIndices{4, NTuple{4, UnitRange{Int64}}}}}:
 [CartesianIndices((1:3, 1:3, 2:2, 1:1)), CartesianIndices((1:3, 1:3, 2:2, 2:2))]
 [CartesianIndices((1:3, 1:3, 3:3, 1:1)), CartesianIndices((1:3, 1:3, 3:3, 2:2))]

julia> feature = rand(3, 2);

julia> feature_selector(feature)
 1-element Vector{Vector{CartesianIndices{2, Tuple{UnitRange{Int64}, UnitRange{Int64}}}}}:
  [CartesianIndices((2:2, 1:1)), CartesianIndices((2:2, 2:2))]
```

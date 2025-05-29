```
BlockRange(axes::Tuple{AbstractUnitRange{Int}})
BlockRange(sizes::Vararg{Integer})
```

Represent a Cartesian range of blocks.

The relationship between `Block` and `BlockRange` mimics the relationship between `CartesianIndex` and `CartesianIndices`.

# Examples

```jldoctest
julia> BlockRange(2:3, 3:4) |> collect
2×2 Matrix{Block{2, Int64}}:
 Block(2, 3)  Block(2, 4)
 Block(3, 3)  Block(3, 4)

julia> BlockRange(2, 2) |> collect # number of elements, starting at 1
2×2 Matrix{Block{2, Int64}}:
 Block(1, 1)  Block(1, 2)
 Block(2, 1)  Block(2, 2)

julia> Block(1):Block(2)
BlockRange(1:2)
```

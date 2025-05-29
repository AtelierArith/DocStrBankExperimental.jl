```
OffsetArray(A, indices...)
```

Return an `AbstractArray` that shares element type and size with the first argument but uses the supplied `indices` to infer its axes. If all the indices are `AbstractUnitRange`s then these are directly used as the axis span along each dimension. Refer to the examples below for other permissible types.

Alternatively it's possible to specify the coordinates of one corner of the array and have the axes be computed automatically from the size of `A`. This constructor makes it convenient to shift to an arbitrary starting index along each axis, for example to a zero-based indexing scheme followed by arrays in languages such as C and Python. See [`Origin`](@ref) and the examples below for this usage.

# Example: offsets

There are two types of `indices`: integers and ranges-like types.

Integers are recognized as offsets, where `0` means no offsets are applied:

```jldoctest; setup=:(using OffsetArrays)
julia> A = OffsetArray(reshape(1:6, 2, 3), -1, -2)
2×3 OffsetArray(reshape(::UnitRange{Int64}, 2, 3), 0:1, -1:1) with eltype Int64 with indices 0:1×-1:1:
 1  3  5
 2  4  6

julia> A[0, 1]
5
```

Examples of range-like types are: `UnitRange` (e.g, `-1:2`), `CartesianIndices`, and `Colon()` (or concisely `:`). A `UnitRange` specifies the axis span along one particular dimension, `CartesianIndices` specify the axis spans along multiple dimensions, and a `Colon` is a placeholder that specifies that the `OffsetArray` shares its axis with its parent along that dimension.

```jldoctest; setup=:(using OffsetArrays)
julia> OffsetArray(reshape(1:6, 2, 3), 0:1, -1:1)
2×3 OffsetArray(reshape(::UnitRange{Int64}, 2, 3), 0:1, -1:1) with eltype Int64 with indices 0:1×-1:1:
 1  3  5
 2  4  6

julia> OffsetArray(reshape(1:6, 2, 3), :, -1:1) # : as a placeholder to indicate that no offset is to be applied to the first dimension
2×3 OffsetArray(reshape(::UnitRange{Int64}, 2, 3), 1:2, -1:1) with eltype Int64 with indices 1:2×-1:1:
 1  3  5
 2  4  6
```

Use `CartesianIndices` to specify the coordinates of two diagonally opposite corners:

```jldoctest; setup=:(using OffsetArrays)
julia> OffsetArray(reshape(1:6, 2, 3), CartesianIndex(0, -1):CartesianIndex(1, 1))
2×3 OffsetArray(reshape(::UnitRange{Int64}, 2, 3), 0:1, -1:1) with eltype Int64 with indices 0:1×-1:1:
 1  3  5
 2  4  6
```

Integers and range-like types may not be combined in the same call:

```julia
julia> OffsetArray(reshape(1:6, 2, 3), 0, -1:1)
ERROR: [...]
```

# Example: origin

[`OffsetArrays.Origin`](@ref) may be used to specify the origin of the OffsetArray. The term origin here refers to the corner with the lowest values of coordinates, such as the left edge for an `AbstractVector`, the bottom left corner for an `AbstractMatrix` and so on. The coordinates of the origin sets the starting index of the array along each dimension.

```jldoctest; setup=:(using OffsetArrays)
julia> a = [1 2; 3 4];

julia> OffsetArray(a, OffsetArrays.Origin(0, 1))
2×2 OffsetArray(::Matrix{Int64}, 0:1, 1:2) with eltype Int64 with indices 0:1×1:2:
 1  2
 3  4

julia> OffsetArray(a, OffsetArrays.Origin(0)) # set the origin to zero along each dimension
2×2 OffsetArray(::Matrix{Int64}, 0:1, 0:1) with eltype Int64 with indices 0:1×0:1:
 1  2
 3  4
```

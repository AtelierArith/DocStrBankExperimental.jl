```
BorderArray(inner::AbstractArray, border::AbstractBorder) <: AbstractArray
```

Construct a thin wrapper around the array `inner`, with given `border`. No data is copied in the constructor, instead border values are computed on the fly in `getindex` calls. Useful for stencil computations. See also [padarray](@ref).

# Examples

```julia
julia> using ImageFiltering

julia> arr = reshape(1:6, (2,3))
2×3 reshape(::UnitRange{Int64}, 2, 3) with eltype Int64:
 1  3  5
 2  4  6

julia> BorderArray(arr, Pad((1,1)))
BorderArray{Int64,2,Base.ReshapedArray{Int64,2,UnitRange{Int64},Tuple{}},Pad{2}} with indices 0:3×0:4:
 1  1  3  5  5
 1  1  3  5  5
 2  2  4  6  6
 2  2  4  6  6

julia> BorderArray(arr, Fill(10, (2,1)))
BorderArray{Int64,2,Base.ReshapedArray{Int64,2,UnitRange{Int64},Tuple{}},Fill{Int64,2}} with indices -1:4×0:4:
 10  10  10  10  10
 10  10  10  10  10
 10   1   3   5  10
 10   2   4   6  10
 10  10  10  10  10
 10  10  10  10  10
```

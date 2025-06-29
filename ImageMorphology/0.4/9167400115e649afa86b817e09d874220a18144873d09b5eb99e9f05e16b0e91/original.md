```
isboundary(img::AbstractArray; background = 0, dims = coords_spatial(A), kwargs...)
```

Finds the boundaries that are just within each object. `background` is the scalar value of the background pixels which will not be marked as boundaries. Keyword arguments are passed to `extremefilt!` which include `dims` indicating the dimension(s) over which to discover boundaries.

See also its in-place version [`isboundary!`](@ref) and the alternative version that finds thick boundaries, [`isboundary_thick`](@ref ImageMorphology.isboundary_thick).

# Examples

```@meta
DocTestSetup = quote
    import ImageMorphology: isboundary
end
```

```jldoctest
julia> A = zeros(Int64, 16, 16); A[4:8, 4:8] .= 5; A[4:8, 9:12] .= 6; A[10:12,13:15] .= 3; A[10:12,3:6] .= 9; A
16×16 Matrix{Int64}:
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  5  5  5  5  5  6  6  6  6  0  0  0  0
 0  0  0  5  5  5  5  5  6  6  6  6  0  0  0  0
 0  0  0  5  5  5  5  5  6  6  6  6  0  0  0  0
 0  0  0  5  5  5  5  5  6  6  6  6  0  0  0  0
 0  0  0  5  5  5  5  5  6  6  6  6  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  9  9  9  9  0  0  0  0  0  0  3  3  3  0
 0  0  9  9  9  9  0  0  0  0  0  0  3  3  3  0
 0  0  9  9  9  9  0  0  0  0  0  0  3  3  3  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0

julia> isboundary(A)
16×16 Matrix{Int64}:
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  1  1  1  1  1  1  1  1  1  0  0  0  0
 0  0  0  1  0  0  0  1  1  0  0  1  0  0  0  0
 0  0  0  1  0  0  0  1  1  0  0  1  0  0  0  0
 0  0  0  1  0  0  0  1  1  0  0  1  0  0  0  0
 0  0  0  1  1  1  1  1  1  1  1  1  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  1  1  1  1  0  0  0  0  0  0  1  1  1  0
 0  0  1  0  0  1  0  0  0  0  0  0  1  0  1  0
 0  0  1  1  1  1  0  0  0  0  0  0  1  1  1  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0

julia> isboundary(A .!= 0)
16×16 BitMatrix:
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  1  1  1  1  1  1  1  1  1  0  0  0  0
 0  0  0  1  0  0  0  0  0  0  0  1  0  0  0  0
 0  0  0  1  0  0  0  0  0  0  0  1  0  0  0  0
 0  0  0  1  0  0  0  0  0  0  0  1  0  0  0  0
 0  0  0  1  1  1  1  1  1  1  1  1  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  1  1  1  1  0  0  0  0  0  0  1  1  1  0
 0  0  1  0  0  1  0  0  0  0  0  0  1  0  1  0
 0  0  1  1  1  1  0  0  0  0  0  0  1  1  1  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0

julia> isboundary(A .!= 0; dims = 1)
16×16 BitMatrix:
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  1  1  1  1  1  1  1  1  1  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  1  1  1  1  1  1  1  1  1  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  1  1  1  1  0  0  0  0  0  0  1  1  1  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  1  1  1  1  0  0  0  0  0  0  1  1  1  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0

julia> isboundary(A .!= 0; dims = 2)
16×16 BitMatrix:
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  1  0  0  0  0  0  0  0  1  0  0  0  0
 0  0  0  1  0  0  0  0  0  0  0  1  0  0  0  0
 0  0  0  1  0  0  0  0  0  0  0  1  0  0  0  0
 0  0  0  1  0  0  0  0  0  0  0  1  0  0  0  0
 0  0  0  1  0  0  0  0  0  0  0  1  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  1  0  0  1  0  0  0  0  0  0  1  0  1  0
 0  0  1  0  0  1  0  0  0  0  0  0  1  0  1  0
 0  0  1  0  0  1  0  0  0  0  0  0  1  0  1  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
 0  0  0  0  0  0  0  0  0  0  0  0  0  0  0  0
```

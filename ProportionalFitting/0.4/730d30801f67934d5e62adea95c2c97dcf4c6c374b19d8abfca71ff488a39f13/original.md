```
ArrayMargins(am::Vector{<:AbstractArray}, di::DimIndices)
ArrayMargins(am::Vector{<:AbstractArray}, di::Vector)
ArrayMargins(am::Vector{<:AbstractArray})
ArrayMargins(X::AbstractArray, di::DimIndices)
ArrayMargins(X::AbstractArray)
```

ArrayMargins are marginal sums of an array, combined with the indices of the dimensions these sums belong to. The marginal sums can be multidimensional arrays themselves.

There are various constructors for ArrayMargins, based on either raw margins or an actual array from which the margins are then computed.

see also: [`DimIndices`](@ref), [`ArrayFactors`](@ref), [`ipf`](@ref)

# Fields

  * `am::Vector{AbstractArray}`: Vector of marginal sums.
  * `di::DimIndices`: Dimension indices to which the elements of `am` belong.

# Examples

```julia-repl
julia> X = reshape(1:12, 2, 3, 2)
2×3×2 reshape(::UnitRange{Int64}, 2, 3, 2) with eltype Int64:
[:, :, 1] =
 1  3  5
 2  4  6

[:, :, 2] =
 7   9  11
 8  10  12

julia> ArrayMargins(X)
Margins from 3D array:
  [1]: [36, 42]
  [2]: [18, 26, 34]
  [3]: [21, 57]

julia> ArrayMargins(X, [1, [2, 3]])
Margins from 3D array:
  [1]: [36, 42]
  [2, 3]: [3 15; 7 19; 11 23]

julia> ArrayMargins(X, [2, [3, 1]])
Margins of 3D array:
  [2]: [18, 26, 34]
  [3, 1]: [9 12; 27 30]
```

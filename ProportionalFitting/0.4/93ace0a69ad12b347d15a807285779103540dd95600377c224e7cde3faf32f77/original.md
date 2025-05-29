```
ArrayFactors(af::Vector{<:AbstractArray}, di::DimIndices)
ArrayFactors(af::Vector{<:AbstractArray}, di::Vector)
ArrayFactors(af::Vector{<:AbstractArray})
```

Array factors are defined such that the array's elements are their products: `M[i, j, ..., l] = af[1][i] * af[2][j] * ... * af[3][l]`.

The array factors can be vectors or multidimensional arrays themselves.

The main use of ArrayFactors is as a memory-efficient representation of a multidimensional array, which can be constructed using the `Array()` method.

see also: [`ipf`](@ref), [`ArrayMargins`](@ref), [`DimIndices`](@ref)

# Fields

  * `af::Vector{<:AbstractArray}`: Vector of (multidimensional) array factors
  * `di::DimIndices`: Dimension indices to which the array factors belong.

# Examples

```julia-repl
julia> AF = ArrayFactors([[1,2,3], [4,5]])
Factors for array of size (3, 2):
  [1]: [1, 2, 3]
  [2]: [4, 5]

julia> eltype(AF)
Int64

julia> Array(AF)
3×2 Matrix{Int64}:
  4   5
  8  10
 12  15

julia> AF = ArrayFactors([[1,2,3], [4 5; 6 7]], DimIndices([2, [1, 3]]))
Factors for 3D array:
  [2]: [1, 2, 3]
  [1, 3]: [4 5; 6 7]

julia> Array(AF)
2×3×2 Array{Int64, 3}:
[:, :, 1] =
 4   8  12
 6  12  18

[:, :, 2] =
 5  10  15
 7  14  21
```

```
tovoigt(A::Union{SecondOrderTensor, FourthOrderTensor}; [order])
tovoigt(A::Union{SymmetricSecondOrderTensor, SymmetricFourthOrderTensor}; [order, offdiagonal])
```

Convert a tensor to Voigt form.

Keyword arguments:

  * `offdiagscale`: Determines the scaling factor for the offdiagonal elements.
  * `order`: A vector of cartesian indices (`Tuple{Int, Int}`) determining the Voigt order. The default order is `[(1,1), (2,2), (3,3), (2,3), (1,3), (1,2), (3,2), (3,1), (2,1)]` for `dim=3`.

See also [`fromvoigt`](@ref).

# Examples

```jldoctest
julia> x = Mat{3,3}(1:9...)
3×3 Tensor{Tuple{3, 3}, Int64, 2, 9}:
 1  4  7
 2  5  8
 3  6  9

julia> tovoigt(x)
9-element StaticArraysCore.SVector{9, Int64} with indices SOneTo(9):
 1
 5
 9
 8
 7
 4
 6
 3
 2

julia> x = SymmetricSecondOrderTensor{3}(1:6...)
3×3 SymmetricSecondOrderTensor{3, Int64, 6}:
 1  2  3
 2  4  5
 3  5  6

julia> tovoigt(x; offdiagscale = 2,
                  order = [(1,1), (2,2), (3,3), (1,2), (1,3), (2,3)])
6-element StaticArraysCore.SVector{6, Int64} with indices SOneTo(6):
  1
  4
  6
  4
  6
 10
```

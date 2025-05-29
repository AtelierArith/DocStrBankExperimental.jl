```
fromvoigt(S::Type{<: Union{SecondOrderTensor, FourthOrderTensor}}, A::AbstractArray{T}; [order])
fromvoigt(S::Type{<: Union{SymmetricSecondOrderTensor, SymmetricFourthOrderTensor}}, A::AbstractArray{T}; [order, offdiagscale])
```

Converts an array `A` stored in Voigt format to a Tensor of type `S`.

Keyword arguments:

  * `offdiagscale`: Determines the scaling factor for the offdiagonal elements.
  * `order`: A vector of cartesian indices (`Tuple{Int, Int}`) determining the Voigt order. The default order is `[(1,1), (2,2), (3,3), (2,3), (1,3), (1,2), (3,2), (3,1), (2,1)]` for `dim=3`.

!!! note
    Since `offdiagscale` is the scaling factor for the offdiagonal elements in **Voigt form**, they are multiplied by `1/offdiagscale` in `fromvoigt` unlike [`tovoigt`](@ref). Thus `fromvoigt(tovoigt(x, offdiagscale = 2), offdiagscale = 2)` returns original `x`.


See also [`tovoigt`](@ref).

# Examples

```jldoctest
julia> fromvoigt(Mat{3,3}, 1.0:1.0:9.0)
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
 1.0  6.0  5.0
 9.0  2.0  4.0
 8.0  7.0  3.0

julia> fromvoigt(SymmetricSecondOrderTensor{3},
                 1.0:1.0:6.0,
                 offdiagscale = 2.0,
                 order = [(1,1), (2,2), (3,3), (1,2), (1,3), (2,3)])
3×3 SymmetricSecondOrderTensor{3, Float64, 6}:
 1.0  2.0  2.5
 2.0  2.0  3.0
 2.5  3.0  3.0
```

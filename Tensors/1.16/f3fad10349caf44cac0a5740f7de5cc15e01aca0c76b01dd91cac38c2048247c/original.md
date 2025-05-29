```
fromvoigt(S::Type{<:AbstractTensor}, A::AbstractArray{T}; kwargs...)
```

Converts an array `A` stored in Voigt format to a Tensor of type `S`.

Keyword arguments:

  * `offset`: offset index for where in the array `A` the tensor starts. For 4th order tensors the keyword arguments are `offset_i` and `offset_j`, respectively. Defaults to `0`.
  * `offdiagscale`: determines the scaling factor for the offdiagonal elements. This argument is only applicable for `SymmetricTensor`s. `frommandel` can also be used for the "Mandel"-format which sets `offdiagscale = √2` for `SymmetricTensor`s, and is equivalent to `fromvoigt` for `Tensor`s.
  * `order`: matrix of the linear indices determining the Voigt order. The default index order is `[11, 22, 33, 23, 13, 12, 32, 31, 21]`, corresponding to `order = [1 6 5; 9 2 4; 8 7 3]`.

See also [`tovoigt`](@ref).

```jldoctest
julia> fromvoigt(Tensor{2,3}, 1.0:1.0:9.0)
3×3 Tensor{2, 3, Float64, 9}:
 1.0  6.0  5.0
 9.0  2.0  4.0
 8.0  7.0  3.0
```

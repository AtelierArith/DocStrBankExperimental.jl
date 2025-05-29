```
tovoigt([type::Type{<:AbstractArray}, ]A::Union{SecondOrderTensor, FourthOrderTensor}; kwargs...)
```

Converts a tensor to "Voigt"-format.

Optional argument:

  * `type`: determines the returned Array type. Possible types are `Array` and `SArray` (see [`StaticArrays`](https://juliaarrays.github.io/StaticArrays.jl/stable/)).

Keyword arguments:

  * `offdiagscale`: determines the scaling factor for the offdiagonal elements. This argument is only applicable for `SymmetricTensor`s. `tomandel` can also be used for the "Mandel"-format which sets `offdiagscale = √2` for `SymmetricTensor`s, and is equivalent to `tovoigt` for `Tensor`s.
  * `order`: matrix of the linear indices determining the Voigt order. The default index order is `[11, 22, 33, 23, 13, 12, 32, 31, 21]`, corresponding to `order = [1 6 5; 9 2 4; 8 7 3]`.

See also [`tovoigt!`](@ref) and [`fromvoigt`](@ref).

```jldoctest
julia> tovoigt(Tensor{2,3}(1:9))
9-element Vector{Int64}:
 1
 5
 9
 8
 7
 4
 6
 3
 2

julia> tovoigt(SymmetricTensor{2,3}(1:6); offdiagscale = 2)
6-element Vector{Int64}:
  1
  4
  6
 10
  6
  4

julia> tovoigt(Tensor{4,2}(1:16))
4×4 Matrix{Int64}:
 1  13   9  5
 4  16  12  8
 3  15  11  7
 2  14  10  6

julia> using StaticArrays: SMatrix

julia> tovoigt(SMatrix, Tensor{4,2}(1:16))
4×4 SMatrix{4, 4, Int64, 16} with indices SOneTo(4)×SOneTo(4):
 1  13   9  5
 4  16  12  8
 3  15  11  7
 2  14  10  6
```

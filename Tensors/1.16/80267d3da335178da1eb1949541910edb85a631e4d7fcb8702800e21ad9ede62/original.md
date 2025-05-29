```
tovoigt!(v::AbstractArray, A::Union{SecondOrderTensor, FourthOrderTensor}; kwargs...)
```

Converts a tensor to "Voigt"-format using the following index order: `[11, 22, 33, 23, 13, 12, 32, 31, 21]`.

Keyword arguments:

  * `offset`: offset index for where in the array `A` the tensor should be stored. For 4th order tensors the keyword arguments are `offset_i` and `offset_j`, respectively. Defaults to `0`.
  * `offdiagscale`: determines the scaling factor for the offdiagonal elements. This argument is only applicable for `SymmetricTensor`s. `frommandel!` can also be used for the "Mandel"-format which sets `offdiagscale = √2` for `SymmetricTensor`s, and is equivalent to `fromvoigt!` for `Tensor`s.
  * `order`: matrix of the linear indices determining the Voigt order. The default index order is `[11, 22, 33, 23, 13, 12, 32, 31, 21]`.

See also [`tovoigt`](@ref) and [`fromvoigt`](@ref).

```jldoctest
julia> T = rand(Tensor{2,2})
2×2 Tensor{2, 2, Float64, 4}:
 0.325977  0.218587
 0.549051  0.894245

julia> x = zeros(4);

julia> tovoigt!(x, T)
4-element Vector{Float64}:
 0.32597672886359486
 0.8942454282009883
 0.21858665481883066
 0.5490511363155669

julia> x = zeros(5);

julia> tovoigt!(x, T; offset=1)
5-element Vector{Float64}:
 0.0
 0.32597672886359486
 0.8942454282009883
 0.21858665481883066
 0.5490511363155669
```

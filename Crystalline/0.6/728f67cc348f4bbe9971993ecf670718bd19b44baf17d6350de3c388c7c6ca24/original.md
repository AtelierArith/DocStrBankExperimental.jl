```
isapprox(v1::T, v2::T, 
         [cntr::Union{Char, Nothing, AbstractMatrix{<:Real}}, modw::Bool];
         kwargs...) --> Bool
```

Compute approximate equality of two vector quantities `v1` and `v2` of type, `T = Union{<:AbstractVec, <:AbstractPoint}`. 

If `modw = true`, equivalence is considered modulo lattice vectors. If `v1` and `v2` are in the conventional setting of a non-primitive lattice, the centering type `cntr` (see [`Bravais.centering`](@ref)) should be given to ensure that the relevant (primitive) lattice vectors are used in the comparison.

## Optional arguments

  * `cntr`: if not provided, the comparison will not account for equivalence by primitive lattice vectors (equivalent to setting `cntr=nothing`), only equivalence by lattice vectors in the basis of `v1` and `v2`. `cntr` may also be provided as a `D`×`D` `AbstractMatrix` to give the relevant transformation matrix directly.
  * `modw`: whether vectors that differ by multiples of a lattice vector are considered equivalent.
  * `kwargs...`: optional keyword arguments (e.g., `atol` and `rtol`) to be forwarded to `Base.isapprox`.

```
InfiniteMPS{A<:GenericMPSTensor,B<:MPSBondTensor} <: AbtractMPS
```

Type that represents an infinite Matrix Product State.

## Fields

  * `AL` – left-gauged MPS tensors
  * `AR` – right-gauged MPS tensors
  * `AC` – center-gauged MPS tensors
  * `C` – gauge tensors

## Notes

By convention, we have that:

  * `AL[i] * C[i]` = `AC[i]` = `C[i-1] * AR[i]`
  * `AL[i]' * AL[i] = 1`
  * `AR[i] * AR[i]' = 1`

---

## Constructors

```
InfiniteMPS([f, eltype], physicalspaces::Vector{<:Union{S, CompositeSpace{S}},
            virtualspaces::Vector{<:Union{S, CompositeSpace{S}};
            kwargs...) where {S<:ElementarySpace}
InfiniteMPS(As::AbstractVector{<:GenericMPSTensor}; kwargs...)
InfiniteMPS(ALs::AbstractVector{<:GenericMPSTensor}, C₀::MPSBondTensor;
            kwargs...)
```

Construct an MPS via a specification of physical and virtual spaces, or from a list of tensors `As`, or a list of left-gauged tensors `ALs`.

### Arguments

  * `As::AbstractVector{<:GenericMPSTensor}`: vector of site tensors
  * `ALs::AbstractVector{<:GenericMPSTensor}`: vector of left-gauged site tensors
  * `C₀::MPSBondTensor`: initial gauge tensor
  * `f::Function=rand`: initializer function for tensor data
  * `eltype::Type{<:Number}=ComplexF64`: scalar type of tensors
  * `physicalspaces::AbstractVector{<:Union{S, CompositeSpace{S}}`: list of physical spaces
  * `virtualspaces::AbstractVector{<:Union{S, CompositeSpace{S}}`: list of virtual spaces

### Keywords

  * `tol`: gauge fixing tolerance
  * `maxiter`: gauge fixing maximum iterations

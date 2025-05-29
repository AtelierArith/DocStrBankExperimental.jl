```
FiniteMPS{A<:GenericMPSTensor,B<:MPSBondTensor} <: AbstractFiniteMPS
```

Type that represents a finite Matrix Product State.

## Properties

  * `AL` – left-gauged MPS tensors
  * `AR` – right-gauged MPS tensors
  * `AC` – center-gauged MPS tensors
  * `C` – gauge tensors
  * `center` – location of the gauge center

The center property returns `center::HalfInt` that indicates the location of the MPS center:

  * `isinteger(center)` → `center` is a whole number and indicates the location of the first `AC` tensor present in the underlying `ψ.ACs` field.
  * `ishalfodd(center)` → `center` is a half-odd-integer, meaning that there are no `AC` tensors, and indicating between which sites the bond tensor lives.

e.g `mps.center = 7/2` means that the bond tensor is to the right of the 3rd site and can be accessed via `mps.C[3]`.

## Notes

By convention, we have that:

  * `AL[i] * C[i]` = `AC[i]` = `C[i-1] * AR[i]`
  * `AL[i]' * AL[i] = 1`
  * `AR[i] * AR[i]' = 1`

---

## Constructors

```
FiniteMPS([f, eltype], physicalspaces::Vector{<:Union{S,CompositeSpace{S}}},
          maxvirtualspaces::Union{S,Vector{S}};
          normalize=true, left=oneunit(S), right=oneunit(S)) where {S<:ElementarySpace}
FiniteMPS([f, eltype], N::Int, physicalspace::Union{S,CompositeSpace{S}},
          maxvirtualspaces::Union{S,Vector{S}};
          normalize=true, left=oneunit(S), right=oneunit(S)) where {S<:ElementarySpace}
FiniteMPS(As::Vector{<:GenericMPSTensor}; normalize=false, overwrite=false)
```

Construct an MPS via a specification of physical and virtual spaces, or from a list of tensors `As`. All cases reduce to the latter. In particular, a state with a non-trivial total charge can be constructed by passing a non-trivially charged vector space as the `left` or `right` virtual spaces.

### Arguments

  * `As::Vector{<:GenericMPSTensor}`: vector of site tensors
  * `f::Function=rand`: initializer function for tensor data
  * `eltype::Type{<:Number}=ComplexF64`: scalar type of tensors
  * `physicalspaces::Vector{<:Union{S, CompositeSpace{S}}`: list of physical spaces
  * `N::Int`: number of sites
  * `physicalspace::Union{S,CompositeSpace{S}}`: local physical space
  * `virtualspaces::Vector{<:Union{S, CompositeSpace{S}}`: list of virtual spaces
  * `maxvirtualspace::S`: maximum virtual space

### Keywords

  * `normalize=true`: normalize the constructed state
  * `overwrite=false`: overwrite the given input tensors
  * `left=oneunit(S)`: left-most virtual space
  * `right=oneunit(S)`: right-most virtual space

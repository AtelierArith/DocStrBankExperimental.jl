```
struct InfiniteWeightPEPS{T<:PEPSTensor,E<:PEPSWeight}
```

Represents an infinite projected entangled-pair state on a 2D square lattice consisting of vertex tensors and bond weights.

## Fields

  * `vertices::Matrix{T} where T<:(TensorKit.AbstractTensorMap{<:Any, S, 1, 4} where S<:TensorKit.ElementarySpace)`
  * `weights::PEPSKit.SUWeight`

## Constructors

```
InfiniteWeightPEPS(vertices::Matrix{T}, weight_mats::Matrix{E}...) where {T<:PEPSTensor,E<:PEPSWeight}
InfiniteWeightPEPS([f=randn, T=ComplexF64,] Pspaces::M, Nspaces::M, [Espaces::M]) where {M<:AbstractMatrix{<:Union{Int,ElementarySpace}}}
InfiniteWeightPEPS([f=randn, T=ComplexF64,] Pspace::S, Nspace::S, Espace::S=Nspace; unitcell::Tuple{Int,Int}=(1, 1)) where {S<:ElementarySpace}
```

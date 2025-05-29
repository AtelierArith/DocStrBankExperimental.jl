```
struct InfiniteWeightPEPS{T<:PEPSTensor,E<:PEPSWeight}
```

2D正方格子上の頂点テンソルとボンド重みからなる無限投影絡み合ったペア状態を表します。

## フィールド

  * `vertices::Matrix{T} where T<:(TensorKit.AbstractTensorMap{<:Any, S, 1, 4} where S<:TensorKit.ElementarySpace)`
  * `weights::PEPSKit.SUWeight`

## コンストラクタ

```
InfiniteWeightPEPS(vertices::Matrix{T}, weight_mats::Matrix{E}...) where {T<:PEPSTensor,E<:PEPSWeight}
InfiniteWeightPEPS([f=randn, T=ComplexF64,] Pspaces::M, Nspaces::M, [Espaces::M]) where {M<:AbstractMatrix{<:Union{Int,ElementarySpace}}}
InfiniteWeightPEPS([f=randn, T=ComplexF64,] Pspace::S, Nspace::S, Espace::S=Nspace; unitcell::Tuple{Int,Int}=(1, 1)) where {S<:ElementarySpace}
```

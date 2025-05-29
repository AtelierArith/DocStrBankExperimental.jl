```julia
struct FRPSpace2D{A, I<:Integer, B, C<:(AbstractVector{<:AbstractFloat}), D<:(AbstractArray{<:AbstractFloat, 5}), E<:(AbstractMatrix{<:AbstractFloat})} <: FluxReconstruction.AbstractStructFRSpace
```

フラックス再構成法のための2D物理空間

# フィールド

  * `base`
  * `deg`
  * `J`
  * `iJ`
  * `Ji`
  * `np`
  * `xpl`
  * `xpg`
  * `wp`
  * `dl`
  * `ll`
  * `lr`
  * `dll`
  * `dlr`
  * `dhl`
  * `dhr`
  * `V`
  * `iV`

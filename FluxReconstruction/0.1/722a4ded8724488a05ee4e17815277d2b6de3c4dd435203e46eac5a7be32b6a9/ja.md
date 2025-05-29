```julia
struct FRPSpace1D{A, I<:Integer, B<:(AbstractVector{<:AbstractFloat}), C<:(AbstractMatrix{<:AbstractFloat})} <: FluxReconstruction.AbstractStructFRSpace
```

フラックス再構成法のための1D物理空間

# フィールド

  * `base`
  * `deg`
  * `J`
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

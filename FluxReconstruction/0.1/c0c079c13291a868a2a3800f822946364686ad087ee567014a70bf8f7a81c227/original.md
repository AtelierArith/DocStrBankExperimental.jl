```julia
struct FRPSpace2D{A, I<:Integer, B, C<:(AbstractVector{<:AbstractFloat}), D<:(AbstractArray{<:AbstractFloat, 5}), E<:(AbstractMatrix{<:AbstractFloat})} <: FluxReconstruction.AbstractStructFRSpace
```

2D physical space for flux reconstruction method

# Fields

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

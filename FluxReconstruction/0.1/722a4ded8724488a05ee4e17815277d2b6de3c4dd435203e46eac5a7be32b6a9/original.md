```julia
struct FRPSpace1D{A, I<:Integer, B<:(AbstractVector{<:AbstractFloat}), C<:(AbstractMatrix{<:AbstractFloat})} <: FluxReconstruction.AbstractStructFRSpace
```

1D physical space for flux reconstruction method

# Fields

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

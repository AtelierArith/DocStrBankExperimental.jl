```
onephoton(b::WaveguideBasis{T,1},ξ::AbstractArray;norm=false) where {T}
```

  * Since `b` only contains a single waveguide, the index of the waveguide is not needed.
  * `ξ` should be `AbstractArray` with length(ξ) == b.nsteps
  * `norm::Bool=false`: If true normalize the resulting wavepacket.

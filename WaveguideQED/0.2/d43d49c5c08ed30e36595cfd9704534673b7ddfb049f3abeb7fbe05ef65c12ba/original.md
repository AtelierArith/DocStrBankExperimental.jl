```
twophoton(b::WaveguideBasis{T,1},ξ::Matrix;norm=false) where {T}
```

# Arguments

  * `b::WaveguideBasis{T,Nw}` contains only one waveguide and no index needed.
  * ξ given as a matrix of dimension `(b.nsteps, b.nsteps)`.
  * `norm::Bool=false`: Toggles whether to normalize the resulting wavepacket.

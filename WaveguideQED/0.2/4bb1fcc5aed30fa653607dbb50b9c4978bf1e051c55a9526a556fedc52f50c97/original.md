```
onephoton(b::WaveguideBasis{T,Nw},i,ξvec;norm=false) where {T,Nw}
```

  * Since `b` contains a `Nw` waveguides, the index of the waveguide needed.
  * `i` is the index of the waveguide at which the onephoton wavepacket is created in
  * `ξ` should be `AbstractArray` with length(ξ) == b.nsteps
  * `norm::Bool=false`: If true normalize the resulting wavepacket.

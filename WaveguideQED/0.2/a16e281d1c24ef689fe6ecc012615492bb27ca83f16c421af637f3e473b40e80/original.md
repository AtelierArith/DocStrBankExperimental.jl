```
onephoton(b::WaveguideBasis{T,Nw},i::Int,ξ::Function,args...; norm=false) where {T,Nw}
```

  * Since `b` contains `Nw` waveguides, the index of the waveguide needed.
  * `i` is the index of the waveguide at which the onephoton wavepacket is created in
  * `ξ` should be broadcastable as ξ.(times,args...), where `times  = 0:b.dt:(b.nsteps-1)*b.dt` (the times used to define the waveguidebasis)
  * `args...`: additional arguments to be passed to ξ if it is a function.
  * `norm::Bool=false`: If true normalize the resulting wavepacket.

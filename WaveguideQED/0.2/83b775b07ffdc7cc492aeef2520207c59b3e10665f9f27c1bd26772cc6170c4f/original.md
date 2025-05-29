```
onephoton(b::WaveguideBasis{T,1},ξ::Function,args...,norm=false) where {T}
```

  * Since `b` only contains a single waveguide, the index of the waveguide is not needed.
  * `ξ` should be broadcastable as ξ.(times,args...), where `times  = 0:b.dt:(b.nsteps-1)*b.dt` (the times used to define the waveguidebasis)
  * `args...`: additional arguments to be passed to ξ if it is a function.
  * `norm::Bool=false`: If true normalize the resulting wavepacket.

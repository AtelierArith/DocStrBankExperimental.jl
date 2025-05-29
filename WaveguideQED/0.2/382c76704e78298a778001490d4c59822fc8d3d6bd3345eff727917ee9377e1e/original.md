```
twophoton(b::WaveguideBasis{T,1},ξ::Function,args...,norm=false) where {T}
```

# Arguments

  * `b::WaveguideBasis{T,Nw}` contains only one waveguide and no index needed.
  * ξ given as a function should follow  `ξ(t1,t2,args...)`,  where `t1` and `t2` are the input times.
  * `args...`: additional arguments to be passed to ξ if it is a function.
  * `norm::Bool=false`: Toggles whether to normalize the resulting wavepacket.

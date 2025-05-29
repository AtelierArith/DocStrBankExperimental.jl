```
twophoton(b::WaveguideBasis{T,Nw},i::Int,j::Int,ξ::Function,args...;norm=false) where {T,Nw}
```

# Arguments

  * `b::WaveguideBasis{T,Nw}` contains multiple waveguides and index i is need.
  * `i` denotes the index of the waveguide in the twophoton state: $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{j}}^\dagger(t') |\emptyset \rangle$.
  * `j` denotes the index of the waveguide in the twophoton state: $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{j}}^\dagger(t') |\emptyset \rangle$.
  * ξ given as a function should follow  `ξ(t1,t2,args...)` where `t1` and `t2` are the input times.
  * `args...`: additional arguments to be passed to ξ.
  * `norm::Bool=false`: Toggles whether to normalize the resulting wavepacket.

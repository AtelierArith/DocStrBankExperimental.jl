```
twophoton(b::WaveguideBasis{T,Nw},idx::I,ξ::Function,times,args...;norm=false) where {T,Nw,I<:Union{Vector{Int64},Tuple{Vararg{Int64}}}} = twophoton(b,idx[1],idx[2],ξ,times,args...,norm=norm)
```

# Arguments

  * `b::WaveguideBasis{T,Nw}` contains multiple waveguides and index i is need.
  * `I[1]` denotes the index $i$ of the waveguide in the twophoton state: $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{j}}^\dagger(t') |\emptyset \rangle$.
  * `I[2]` denotes the index $j$ of the waveguide in the twophoton state: $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{j}}^\dagger(t') |\emptyset \rangle$.
  * ξ given as a function should follow  `ξ(times[l],times[m],args...)`.
  * `times`: A vector or range of length(times) = b.nsteps.
  * `args...`: additional arguments to be passed to ξ.
  * `norm::Bool=false`: Toggles whether to normalize the resulting wavepacket.

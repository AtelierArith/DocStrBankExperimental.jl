```
twophoton(b::WaveguideBasis{T,Nw},idx::I,ξ::Matrix;norm=false) where {T,Nw,I<:Union{Vector{Int64},Tuple{Vararg{Int64}}}}
```

# Arguments

  * `b::WaveguideBasis{T,Nw}` contains multiple waveguides and index i is need.
  * `I[1]` denotes the index $i$ of the waveguide in the twophoton state: $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{j}}^\dagger(t') |\emptyset \rangle$.
  * `I[2]` denotes the index $j$ of the waveguide in the twophoton state: $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{j}}^\dagger(t') |\emptyset \rangle$.
  * ξ given as a matrix of dimension `(b.nsteps, b.nsteps)`.
  * `norm::Bool=false`: Toggles whether to normalize the resulting wavepacket.

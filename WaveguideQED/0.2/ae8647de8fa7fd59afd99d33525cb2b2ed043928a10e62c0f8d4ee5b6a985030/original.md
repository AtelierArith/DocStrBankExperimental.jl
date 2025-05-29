```
twophoton(b::WaveguideBasis{T,Nw},i::Int,ξ::Matrix;norm=false) where {T,Nw}
```

# Arguments

  * `b::WaveguideBasis{T,Nw}` contains multiple waveguides and index i is need.
  * `i` denotes the index of the waveguide in the twophoton state: $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{i}}^\dagger(t') |\emptyset \rangle$.
  * ξ given as a matrix of dimension `(b.nsteps, b.nsteps)`.
  * `norm::Bool=false`: Toggles whether to normalize the resulting wavepacket.

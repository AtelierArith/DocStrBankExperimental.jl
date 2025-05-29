```
OnePhotonView(ψ::T) where {T<:SingleWaveguideKet}
```

ψ contains only a single waveguide and no waveguide index is needed. No index of the system is provided and groundstate is assumed.  Thus returns `OnePhotonView(ψ,index)` with `index = [1,:,1,...]` with `:` at the location of the waveguide and 1 in every other position. 

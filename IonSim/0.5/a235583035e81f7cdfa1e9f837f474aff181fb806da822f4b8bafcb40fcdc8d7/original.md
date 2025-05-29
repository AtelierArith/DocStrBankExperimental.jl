```
Laser(;λ=missing, E=0, Δ=0, ϵ=(x̂+ŷ)/√2, k=ẑ, ϕ=0, pointing::Array{Tuple{Int,Real}})
```

The physical parameters defining laser light. **args**

  * `λ::Union{Real,Missing}`: the wavelength of the laser in meters
  * `I::Union{Function,Real}`: laser intensity in W/m²
  * `Δ`: static detuning from f = c/λ in [Hz]
  * `ϵ::NamedTuple`: (ϵ.x, ϵ.y, ϵ.z), polarization direction, requires norm of 1
  * `k::NamedTuple`: (k.x, k.y, k.z), propagation direction, requires norm of 1
  * `ϕ::Union{Function,Real}`: time-dependent phase. of course, this can also be used to model a    time-dependent detuning. Units are in radians. Note: if this is set to a function of time,   then when constructing a Hamiltonian with the `hamiltonian` function, the units of time   will be as specified by the `timescale` keyword argument.
  * `pointing`: an array of `Tuple{Int,Real}` for describing ion-laser pointing configuration.   (first element of the tuple is the index for an ion and the second element is the scaling   factor for the laser's Efield which must be between 0 and 1).

```
GenericFluor <: Molecule
```

Defines a fluorophore with photophysical properties.

# Fields

  * `γ::AbstractFloat`: Photon emission rate in Hz. Default: 1e5
  * `q::Array{<:AbstractFloat}`: Rate matrix where q[i,j] for i≠j is the transition rate from state i to j, and q[i,i] is the negative exit rate from state i. Default: standard 2-state model with on->off rate of 50Hz and off->on rate of 1e-2Hz

# Examples

```julia
# Create a fluorophore with default parameters (using the 2-state keyword constructor)
fluor = GenericFluor()

# Create a fluorophore with custom parameters using the positional constructor
fluor = GenericFluor(1e5, [-50.0 50.0; 1e-2 -1e-2])

# Create a fluorophore using the 2-state keyword constructor
fluor = GenericFluor(; photons=1e5, k_off=10.0, k_on=1e-1)
```

```
GenericFluor(; photons::AbstractFloat=1e5, k_off::AbstractFloat=50.0, k_on::AbstractFloat=1e-2)
```

Create a simple two-state (on/off) fluorophore with specified parameters.

# Arguments

  * `photons::AbstractFloat`: Photon emission rate in Hz
  * `k_off::AbstractFloat`: Off-switching rate (on→off) in Hz
  * `k_on::AbstractFloat`: On-switching rate (off→on) in Hz

# Details

Creates a fluorophore with a 2-state model and the specified rates. State 1 is the on (bright) state, and state 2 is the off (dark) state. The rate matrix is constructed as: q = [-k*off k*off; k*on -k*on]

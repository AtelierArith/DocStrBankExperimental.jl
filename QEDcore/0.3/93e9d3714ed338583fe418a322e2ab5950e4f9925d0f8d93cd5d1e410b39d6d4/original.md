```julia
mutable struct MFourMomentum <: QEDbase.AbstractFourMomentum
```

Builds a mutable LorentzVector with real components used to statically model the four-momentum of a particle or field.

# Fields

  * `E::Float64`: energy component
  * `px::Float64`: `x` component
  * `py::Float64`: `y` component
  * `pz::Float64`: `z` component

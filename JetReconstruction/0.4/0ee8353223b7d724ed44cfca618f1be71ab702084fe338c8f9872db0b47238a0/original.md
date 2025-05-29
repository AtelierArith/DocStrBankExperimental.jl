```
mutable struct EEjet
```

The `EEjet` struct is a 4-momentum object used for the e+e jet reconstruction routines.

# Fields

  * `px::Float64`: The x-component of the jet momentum.
  * `py::Float64`: The y-component of the jet momentum.
  * `pz::Float64`: The z-component of the jet momentum.
  * `E::Float64`: The energy of the jet.
  * `_cluster_hist_index::Int`: The index of the cluster histogram.
  * `_p2::Float64`: The squared momentum of the jet.
  * `_inv_p::Float64`: The inverse momentum of the jet.

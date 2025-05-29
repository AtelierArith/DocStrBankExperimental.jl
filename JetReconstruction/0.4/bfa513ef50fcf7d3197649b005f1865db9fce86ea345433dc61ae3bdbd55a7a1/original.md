```
mutable struct PseudoJet <: FourMomentum
```

The `PseudoJet` struct represents a pseudojet, a four-momentum object used in jet reconstruction algorithms. Additional information for the link back into the history of the clustering is stored in the `_cluster_hist_index` field. There is caching of the more expensive calculations for rapidity and azimuthal angle.

# Fields

  * `px::Float64`: The x-component of the momentum.
  * `py::Float64`: The y-component of the momentum.
  * `pz::Float64`: The z-component of the momentum.
  * `E::Float64`: The energy component of the momentum.
  * `_cluster_hist_index::Int`: The index of the cluster history.
  * `_pt2::Float64`: The squared transverse momentum.
  * `_inv_pt2::Float64`: The inverse squared transverse momentum.
  * `_rap::Float64`: The rapidity.
  * `_phi::Float64`: The azimuthal angle.

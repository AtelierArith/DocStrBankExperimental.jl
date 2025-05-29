```
ODProblem{D, T <: Real, WT <: AbstractWeightingScheme{T},
    DT <: AbstractDebiasingScheme{T}}
```

An orbit determination problem.

## Fields

  * `dynamics::D`: dynamical model.
  * `radec::Vector{RadecMPC{T}}`: vector of optical astrometry.
  * `tracklets::Vector{Tracklet{T}}`: vector of tracklets.
  * `w8s::WT`: weighting scheme.
  * `bias::DT`: debiasing scheme.

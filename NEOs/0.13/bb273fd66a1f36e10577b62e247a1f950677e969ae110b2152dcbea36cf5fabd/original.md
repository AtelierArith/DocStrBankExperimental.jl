```
ODProblem(dynamics::D, radec::Vector{RadecMPC{T}} [,
    w8s::WT [, bias::DT]]) where {D, T <: Real, WT, DT}
```

Return an orbit determination problem.

## Arguments

  * `dynamics::D`: dynamical model.
  * `radec::Vector{RadecMPC{T}}`: vector of optical astrometry.
  * `w8s::WT`: weighting scheme (default: `Veres17`).
  * `bias::DT`: debiasing scheme (default: `Eggl20`).

```julia
struct DERelative{T<:DistributedFactorGraphs.InferenceVariable, P, D} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

Build a full ODE solution into a relative factor to condense possible sensor data into a relative transformation, but keeping the parameter estimation process fluid.  Assumes first and second variable in order  are of same dimension and compatible manifolds, such that ODE runs from Xi to Xi+1 on all dimensions.  Internal state vector can be decoupled onto different domain as needed.

Notes

  * Based on DifferentialEquations.jl
  * `getSample` step does the `solve(ODEProblem)` step.
  * `tspan` is taken from variables only once at object construction – i.e. won't detect changed timestamps.
  * Regular factor evaluation is done as full dimension `AbstractRelativeRoots`, and is basic linear difference.

DevNotes

  * FIXME see 1025, `multihypo=` will not yet work.
  * FIXME Lots of consolidation and standardization to do, see RoME.jl #244 regarding Manifolds.jl.
  * TODO does not yet handle case where a factor spans across two timezones.

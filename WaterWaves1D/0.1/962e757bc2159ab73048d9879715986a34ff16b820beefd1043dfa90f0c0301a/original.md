```
SolitaryWaveSerreGreenNaghdi(param; x₀=0)
```

Compute the Serre-Green-Naghdi solitary wave with prescribed velocity.

# Arguments

  * `param :: NamedTuple`: parameters of the problem containing velocity `c` and dimensionless parameters `ϵ` and `μ`, and mesh size `L` and number of collocation points `N`;
  * `x₀ :: Real`: (keyword, optional, default = 0) center of solitary wave.

# Return values

`(η,u,v,mesh)` with

  * `η :: Vector{Float64}`: surface deformation;
  * `u :: Vector{Float64}`: layer-averaged velocity;
  * `v :: Vector{Float64}`: derivative of the trace of the velocity potential at the surface;
  * `mesh :: Mesh`: mesh collocation points.

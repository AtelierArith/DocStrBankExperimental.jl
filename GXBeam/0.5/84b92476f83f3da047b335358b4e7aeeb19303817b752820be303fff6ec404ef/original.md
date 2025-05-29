```
DistributedLoads(assembly, ielem; kwargs...)
```

Pre-integrate distributed loads on a beam element for use in an analysis.

# Arguments

  * `assembly`: Beam element assembly (of type [`Assembly`](@ref))
  * `ielem`: Beam element index

# Keyword Arguments

  * `s1 = 0.0`: Start of the beam element (used solely for integrating the distributed loads)
  * `s2 = 1.0`: End of the beam element (used solely for integrating the distributed loads)
  * `method = (f, s1, s2) -> gauss_quadrature(f, s1, s2)`: Method which integrates function

`f` from `s1` to `s2`. Defaults to the Gauss-Legendre quadrature with 4 points on each element.

  * `fx = (s) -> 0.0`: Distributed x-direction force
  * `fy = (s) -> 0.0`: Distributed y-direction force
  * `fz = (s) -> 0.0`: Distributed z-direction force
  * `mx = (s) -> 0.0`: Distributed x-direction moment
  * `my = (s) -> 0.0`: Distributed y-direction moment
  * `mz = (s) -> 0.0`: Distributed z-direction moment
  * `fx_follower = (s) -> 0.0`: Distributed x-direction follower force
  * `fy_follower = (s) -> 0.0`: Distributed y-direction follower force
  * `fz_follower = (s) -> 0.0`: Distributed z-direction follower force
  * `mx_follower = (s) -> 0.0`: Distributed x-direction follower moment
  * `my_follower = (s) -> 0.0`: Distributed y-direction follower moment
  * `mz_follower = (s) -> 0.0`: Distributed z-direction follower moment

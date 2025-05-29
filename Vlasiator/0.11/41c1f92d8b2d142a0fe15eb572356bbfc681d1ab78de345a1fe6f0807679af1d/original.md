```
find_reconnection_points(ψ::Array{T,2}; retol::Float64=1e-4,
   method::Int=1) -> indices_x, indices_o
```

Find X-point and O-point indices in 2D magnetic field topology from flux function `ψ`. The current implementation does not work for the 3 layers near the boundary.

# Keywords

  * `retol=1e-1`: determines the relative tolerance of the ratio w.r.t. |∇ψ|² to accept a gradient as 0.
  * `method=1`: method 1 compute the cell-centered 1st and 2nd order derivatives and check the Hessian matrix; method 2 check the flux function at each point against its 8 neighbors, which is more deterministic.

```
SolitaryWaveWhitham(param; kwargs)
```

Compute the Whitham solitary wave with prescribed velocity.

# Argument

  * `param :: NamedTuple`: parameters of the problem containing velocity `c` and dimensionless parameters `ϵ` and `μ`, and mesh size `L` and number of collocation points `N`;

## Keywords (optional)

  * `guess :: Vector{Real}`: initial guess for the surface deformation (if not provided, the exact formula for KdV is used);
  * `x₀ :: Real`: center of solitary wave (if guess is not provided);
  * `iterative :: Bool`: inverts Jacobian through GMRES if `true`, LU decomposition if `false`;
  * `verbose :: Bool`: prints numerical errors at each step if `true`;
  * `max_iter :: Int`: maximum number of iterations of the Newton algorithm;
  * `tol :: Real`: general tolerance (default is `1e-10`);
  * `ktol :: Real`: tolerance of the Krasny filter (default is `0`, i.e. no filtering);
  * `gtol :: Real`: relative tolerance of the GMRES algorithm (default is `1e-10`);
  * `dealias :: Int`: dealiasing with Orlicz rule `1-dealias/(dealias+2)` (default is `0`, i.e. no dealiasing);
  * `q :: Real`: Newton algorithm modified with

`u_{n+1}=q*u_{n+1}+(1-q)*u_n` (default is `1`);

  * `α :: Real`: adds `α` times spectral projection onto the Kernel to the Jacobian;
  * `KdV :: Bool`: if `true` computes the KdV (instead of Whitham) solitary wave.

# Return values

`(u,mesh)` with

  * `u :: Vector{Float64}`: the solution;
  * `mesh :: Mesh`: mesh collocation points.

```
SolitaryWaveWhithamGreenNaghdi(param; kwargs)
```

Compute the Whitham-Green-Naghdi solitary wave with prescribed velocity.

# Arguments

  * `param :: NamedTuple`: parameters of the problem containing velocity `c` and dimensionless parameters `ϵ` and `μ`, and mesh size `L` and number of collocation points `N`;

## Keywords (optional)

  * `guess :: Vector{Real}`: initial guess for the surface deformation (if not provided, the exact formula for SGN is used);
  * `x₀ :: Real`: center of solitary wave (if guess is not provided);
  * `SGN :: Bool`: if `true` computes the Serre-Green-Naghdi (instead of Whitham-Green-Naghdi) solitary wave (consider `SolitaryWaveSerreGreenNaghdi` instead);
  * `method :: Int`: equation used (between `1` and `4`);
  * `iterative :: Bool`: inverts Jacobian through GMRES if `true`, LU decomposition if `false` (default is `false`);
  * `verbose :: Bool`: prints numerical errors at each step if `true` (default is `false`);
  * `max_iter :: Int`: maximum number of iterations of the Newton algorithm (default is `20`);
  * `tol :: Real`: relative tolerance measured in ℓ∞ norm (default is `1e-10`);
  * `ktol :: Real`: tolerance of the Krasny filter (default is `0`, i.e. no filtering);
  * `gtol :: Real`: relative tolerance of the GMRES algorithm (default is `1e-10`);
  * `dealias :: Int`: dealiasing with Orlicz rule `1-dealias/(dealias+2)` (default is `0`, i.e. no dealiasing);
  * `q :: Real`: Newton algorithm modified with `u_{n+1}=q*u_{n+1}+(1-q)*u_n` (default is `1`);
  * `α :: Real`: adds `α` times spectral projection onto the Kernel to the Jacobian (default is `0`).

# Return values

`(η,u,v,mesh)` with

  * `η :: Vector{Float64}`: surface deformation;
  * `u :: Vector{Float64}`: layer-averaged velocity;
  * `v :: Vector{Float64}`: derivative of the velocity potential at the surface;
  * `mesh :: Mesh`: mesh collocation points.

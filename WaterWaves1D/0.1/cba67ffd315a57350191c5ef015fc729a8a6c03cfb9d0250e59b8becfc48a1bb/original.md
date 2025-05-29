```
SolitaryWaveWhithamBoussinesq(param; kwargs)
```

Compute the Whitham-Boussinesq solitary wave with prescribed velocity.

# Argument

  * `param :: NamedTuple`: parameters of the problem containing velocity `c` and dimensionless parameters `ϵ` and `μ`,

and mesh size `L` and number of collocation points `N`;

## Keywords (optional)

  * `guess :: Vector{Real}`: initial guess for the surface deformation (if not provided, the exact formula for SGN is used);
  * `x₀ :: Real`: center of solitary wave (if guess is not provided);
  * `α :: Real`: determines the model used (typically `1` or `1/2`, default is 1);
  * `Boussinesq`: if `true` (default is `false`), compute the standard Boussinesq system with parameters `a` (defaut `-1//3`), `b=d` (defaut `1//3`), and `c=0`);
  * `iterative :: Bool`: inverts Jacobian through GMRES if `true`, LU decomposition if `false`;
  * `verbose :: Bool`: prints numerical errors at each step if `true`;
  * `max_iter :: Int`: maximum number of iterations of the Newton algorithm;
  * `tol :: Real`: general tolerance (default is `1e-10`);
  * `ktol :: Real`: tolerance of the Krasny filter (default is `0`, i.e. no filtering);
  * `gtol :: Real`: relative tolerance of the GMRES algorithm (default is `1e-10`);
  * `dealias :: Int`: dealiasing with Orlicz rule `1-dealias/(dealias+2)` (default is `0`, i.e. no dealiasing);
  * `q :: Real`: Newton algorithm modified with

`u_{n+1}=q*(u_n+du)+(1-q)*u_n` (default is `1`);

  * `β :: Real`: adds `β` times spectral projection onto the Kernel to the Jacobian.β

# Return values

`(η,v,mesh)` with

  * `η :: Vector{Float64}`: surface deformation;
  * `v :: Vector{Float64}`: velocity (derivative of the trace of the velocity potential at the surface);
  * `mesh :: Mesh`: mesh collocation points.

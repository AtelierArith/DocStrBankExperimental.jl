```
WaterWaves(param; kwargs)
```

Define an object of type `AbstractModel` in view of solving the initial-value problem for the water waves system (via conformal mapping, see [Zakharov, Dyachenko and Vasilyev](https://doi.org/10.1016/S0997-7546(02)01189-5)).

# Argument

`param` is of type `NamedTuple` and must contain

  * dimensionless parameters `ϵ` (nonlinearity) and `μ` (dispersion);
  * optionally, `ν` the shallow/deep water scaling factor. By default, `ν=1` if `μ≦1` and `ν=1/√μ` otherwise. Set the infinite-layer case if `ν=0`, or `μ=Inf`.
  * numerical parameters to construct the mesh of collocation points, if `mesh` is not provided as a keyword argument.

## Optional keyword arguments

  * `IL`: Set the infinite-layer case if `IL=true`, in which case `ϵ` is the steepness parameter. Default is `false`.
  * `mesh`: the mesh of collocation points. By default, `mesh = Mesh(param)`;
  * `method ∈ {1,2,3}`: method used to initialize the conformal mapping, as a fix-point problem `F(u)=u`

      * if `method == 1`, use standard contraction fix-point iteration;
      * if `method == 2`, use Newton algorithm with GMRES iterative solver to invert the Jacobian;
      * if `method == 3`, use Newton algorithm with direct solver to invert the Jacobian;
  * `tol`: (relative) tolerance of the fix-point algorithm (default is `1e-16`);
  * `maxiter`: the maximal number of iteration in the fix-point algorithm (default is `100`);
  * `ktol`: tolerance of the low-pass Krasny filter (default is `0`, i.e. no filtering);
  * `dealias`: dealiasing with Orlicz rule `1-dealias/(dealias+2)` (default is `0`, i.e. no dealiasing);
  * `label`: a label for future references (default is `"water waves"`);
  * `verbose`: prints information if `true` (default is `true`).

# Return values

Generate necessary ingredients for solving an initial-value problem via `solve!`:

1. a function `WaterWaves.f!` to be called in the explicit time-integration solver (also `WaterWaves.f1!` and `WaterWaves.f2!` for the symplectic Euler solver);
2. a function `WaterWaves.mapto` which from `(η,v)` of type `InitialData` provides the raw data matrix on which computations are to be executed;
3. a function `WaterWaves.mapfro` which from such data matrix returns the Tuple of real vectors `(η,v,x)`, where

      * `x` is a vector of collocation points (non-regularly spaced);

```
- `η` is the values of surface deformation at collocation points `x`;
- `v` is the derivative of the trace of the velocity potential at `x`.
```

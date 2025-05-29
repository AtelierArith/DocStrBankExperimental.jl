```
WhithamBoussinesq(param;kwargs)
```

Define an object of type `AbstractModel` in view of solving the initial-value problem for a Boussinesq-type model with full-dispersion property.

# Argument

`param` is of type `NamedTuple` and must contain

  * dimensionless parameters `ϵ` (nonlinearity) and `μ` (dispersion);
  * numerical parameters to construct the mesh of collocation points, if `mesh` is not provided as a keyword argument.

## Optional keyword arguments

  * `Boussinesq`: if `true` (default is `false`), compute the standard Boussinesq system instead (see `Boussinesq(param;kwargs)`);
  * a parameter `α` which determines the model solved:

      * If `α = 1` (default), then the model has been introduced in [Dinvay, Dutykh and Kalisch](https://doi.org/10.1016/j.apnum.2018.09.016);
      * If `α = 1/2`, then the model is a quasilinear version;
      * If `α < 1/2`, then expect instabilities stemming from ill-posedness of the model.
  * `mesh`: the mesh of collocation points. By default, `mesh = Mesh(param)`;
  * `ktol`: tolerance of the low-pass Krasny filter (default is `0`, i.e. no filtering);
  * `dealias`: dealiasing with Orlicz rule `1-dealias/(dealias+2)` (default is `0`, i.e. no dealiasing);
  * `label`: a label for future references (default is `"Whitham-Boussinesq"`);

# Return values

Generate necessary ingredients for solving an initial-value problem via `solve!`:

1. a function `WhithamBoussinesq.f!` to be called in explicit time-integration solvers;
2. a function `WhithamBoussinesq.mapto` which from `(η,v)` of type `InitialData` provides the raw data matrix on which computations are to be executed.
3. a function `WhithamBoussinesq.mapfro` which from such data matrix returns the Tuple of real vectors `(η,v,x)`, where

```
- `η` is the values of surface deformation at collocation points `x`;
- `v` is the derivative of the trace of the velocity potential at `x`.
```

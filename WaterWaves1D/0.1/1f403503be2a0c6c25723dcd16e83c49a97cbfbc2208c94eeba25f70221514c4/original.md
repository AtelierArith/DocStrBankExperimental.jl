```
IsobeKakinuma(param;kwargs)
```

Define an object of type `AbstractModel` in view of solving the initial-value problem for the Isobe-Kakinuma model proposed by [Isobe](https://doi.org/10.1061/9780784400890.023).

# Argument

`param` is of type `NamedTuple` (or a collection `NamedTuple`s) of and must contain

  * dimensionless parameters `ϵ` (nonlinearity) and `μ` (dispersion);
  * numerical parameters to construct the mesh of collocation points, if `mesh` is not provided as a keyword argument.

## Optional keyword arguments

  * `mesh`: the mesh of collocation points. By default, `mesh = Mesh(param)`;
  * `iterative`: solve the elliptic problem through GMRES if `true`, LU decomposition if `false` (default is `true`);
  * `precond`: use a (left) preconditioner for GMRES if `true` (default), choose `precond` as the preconditioner if provided;
  * `gtol`: relative tolerance of the GMRES algorithm (default is `1e-14`);
  * `restart`: the corresponding option of the GMRES algorithm (default is `100`);
  * `maxiter`: the corresponding option of GMRES (default is `nothing`);
  * `ktol`: tolerance of the Krasny filter (default is `0`, i.e. no filtering);
  * `dealias`: dealiasing with Orlicz rule `1-dealias/(dealias+2)` (default is `0`, i.e. no dealiasing);
  * `label`: a label for future references (default is `"Isobe-Kakinuma"`);

# Return values

Generate necessary ingredients for solving an initial-value problem via `solve!`:

1. a function `IsobeKakinuma.f!` to be called in explicit time-integration solvers;
2. a function `IsobeKakinuma.mapto` which from `(η,v)` of type `InitialData` provides the raw data matrix on which computations are to be executed;
3. a function `IsobeKakinuma.mapfro` which from such data matrix returns the Tuple of real vectors `(η,v,x)`, where

      * `η` is the values of surface deformation at collocation points `x`;
      * `v` is the derivative of the trace of the velocity potential at `x`.

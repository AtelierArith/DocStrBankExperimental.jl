```
Choi(param;kwargs)
```

Define an object of type `AbstractModel` in view of solving the initial-value problem for the model proposed by [Choi](https://doi.org/10.1017/jfm.2022.544).

# Argument

`param` is of type `NamedTuple` and must contain

  * dimensionless parameters `ϵ` (nonlinearity) and `μ` (dispersion);
  * numerical parameters to construct the mesh of collocation points, if `mesh` is not provided as a keyword argument.

## Optional keyword arguments

  * `M∈{0,1,2}`: the order of the model. `M=2` by default;
  * `reg`: applies a regularization operator. `reg=false` by default.
  * `mesh`: the mesh of collocation points. By default, `mesh = Mesh(param)`;
  * `iterative`: solve the elliptic problem through GMRES if `true`, LU decomposition if `false` (default is `true`);
  * `precond`: use a (left) preconditioner for GMRES if `true` (default), choose `precond` as the preconditioner if provided;
  * `gtol`: relative tolerance of the GMRES algorithm (default is `1e-14`);
  * `restart`: the corresponding option of the GMRES algorithm (default is `100`);
  * `maxiter`: the corresponding option of GMRES (default is `nothing`);
  * `ktol`: tolerance of the Krasny filter (default is `0`, i.e. no filtering);
  * `dealias`: dealiasing with Orlicz rule `1-dealias/(dealias+2)` (default is `0`, i.e. no dealiasing);
  * `label`: a label for future references (default is `"Choi-N"`);

# Return values

Generate necessary ingredients for solving an initial-value problem via `solve!`:

1. a function `Choi.f!` to be called in explicit time-integration solvers;
2. a function `Choi.mapto` which from `(η,v)` of type `InitialData` provides the raw data matrix on which computations are to be executed;
3. a function `Choi.mapfro` which from such data matrix returns the Tuple of real vectors `(η,v,x)`, where

```
- `η` is the values of surface deformation at collocation points `x`;
- `v` is the derivative of the trace of the velocity potential;
```

4. additionally, a handy function `Choi.mapfrofull` which from data matrix returns the Tuple of real vectors `(η,v,u,vᵦ)`, where

```
- `v` is the derivative of the trace of the velocity potential;
- `u` corresponds to the layer-averaged horizontal velocity;
- `vᵦ` corresponds to the horizontal velocity at the bottom.
```

```
relaxedGreenNaghdi(param;kwargs)
```

Define an object of type `AbstractModel` in view of solving the initial-value problem for a relaxed Green-Naghdi model proposed by [N. Favrie and S. Gavrilyuk](https://doi.org/10.1088/1361-6544/aa712d)  or [C. Escalante, M. Dumbser and M. Castro](https://doi.org/10.1016/j.jcp.2019.05.035)  and [G. Richard](https://doi.org/10.1016/j.euromechflu.2021.05.011).

# Argument

`param` is of type `NamedTuple` and must contain

  * dimensionless parameters `ϵ` (nonlinearity) and `μ` (dispersion);
  * the relaxation parameter `a`;
  * numerical parameters to construct the mesh of collocation points, if `mesh` is not provided as a keyword argument.

## Optional keyword arguments

  * `FG`: if `true` (default is `false`), compute the Favrie-Gavrilyuk model, otherwise compute the Escalante-Dumbser-Castro model;
  * `id`: `∈{0,1,2}` and represent the level of preparation of the initial data (default is `1`);
  * `mesh`: the mesh of collocation points. By default, `mesh = Mesh(param)`;
  * `iterative`: solve the elliptic problem (to construct initial data) through GMRES if `true`, LU decomposition if `false` (default is `true`);
  * `precond`: use a (left) preconditioner for GMRES if `true` (default), choose `precond` as the preconditioner if provided;
  * `gtol`: relative tolerance of the GMRES algorithm (default is `1e-14`);
  * `restart`: the corresponding option of the GMRES algorithm (default is `100`);
  * `maxiter`: the corresponding option of GMRES (default is `nothing`);
  * `ktol`: tolerance of the Krasny filter (default is `0`, i.e. no filtering);
  * `dealias`: dealiasing with Orlicz rule `1-dealias/(dealias+2)` (default is `0`, i.e. no dealiasing);
  * `label`: a label for future references (default is `"Favrie-Gavrilyuk"` if `FG==true`, `"Escalante-Dumbser-Castro"` otherwise);

# Return values

Generate necessary ingredients for solving an initial-value problem via `solve!`:

1. a function `relaxedGreenNaghdi.f!` to be called in explicit time-integration solvers;
2. a function `relaxedGreenNaghdi.mapto` which from `(η,v)` of type `InitialData` provides the raw data matrix on which computations are to be executed;
3. a function `relaxedGreenNaghdi.mapfro` which from such data matrix returns the Tuple of real vectors `(η,v,x)`, where

```
- `η` is the values of surface deformation at collocation points `x`;
- `v` is the derivative of the trace of the velocity potential at `x`;
```

4. additionally, a handy function `relaxedGreenNaghdi.mapfrofull` which from data matrix returns the Tuple of real vectors `(η,v,u,p,w)`, where

```
- `u` corresponds to the layer-averaged horizontal velocity.
- `p` corresponds to the relaxed (artificial) layer-averaged non-hydrostatic pressure;
- `w` corresponds to the relaxed (artificial) layer-averaged vertical velocity.
```

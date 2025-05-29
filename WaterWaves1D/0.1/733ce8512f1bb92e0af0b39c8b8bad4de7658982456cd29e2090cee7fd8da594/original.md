```
SaintVenant(param;kwargs)
```

Define an object of type `AbstractModel` in view of solving the initial-value problem for Saint-Venant (or shallow water) model.

# Argument

`param` is of type `NamedTuple` and must contain

  * the dimensionless parameter `ϵ` (nonlinearity);
  * numerical parameters to construct the mesh of collocation points, if `mesh` is not provided as a keyword argument.

## Optional keyword arguments

  * `mesh`: the mesh of collocation points. By default, `mesh = Mesh(param)`;
  * `ktol`: tolerance of the low-pass Krasny filter (default is `0`, i.e. no filtering);
  * `dealias`: no dealisasing if set to `0` or `false` (default), standard 3/2 Orlicz rule if set to `1` or `true`, otherwise the value sets additionnally a maximal slope of the dealiasing symbol (`2/dealias` models are affected);
  * `label`: a label for future references (default is `"Saint-Venant"`);

# Return values

Generate necessary ingredients for solving an initial-value problem via `solve!`:

1. a function `SaintVenant.f!` to be called in explicit time-integration solvers;
2. a function `SaintVenant.mapto` which from `(η,v)` of type `InitialData` provides the raw data matrix on which computations are to be executed;
3. a function `SaintVenant.mapfro` which from such data matrix returns the Tuple of real vectors `(η,v,x)`, where

      * `η` is the values of surface deformation at collocation points `x`;
      * `v` is the derivative of the trace of the velocity potential at `x`.

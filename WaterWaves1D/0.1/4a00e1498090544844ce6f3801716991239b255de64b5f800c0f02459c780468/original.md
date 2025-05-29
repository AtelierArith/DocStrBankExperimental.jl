```
modifiedMatsuno(param;kwargs)
```

Define an object of type `AbstractModel` in view of solving the initial-value problem for the modified Matsuno model proposed by [Duchêne and Melinand](https://arxiv.org/abs/2203.03277).

# Argument

`param` is of type `NamedTuple` and must contain

  * dimensionless parameters `ϵ` (nonlinearity) and `μ` (dispersion);
  * optionally, `ν` the shallow/deep water scaling factor. By default, `ν=1` if `μ≦1` and `ν=1/√μ` otherwise. Set the infinite-layer case if `ν=0`, or `μ=Inf`.
  * numerical parameters to construct the mesh of collocation points, if `mesh` is not provided as a keyword argument.

## Optional keyword arguments

  * `IL`: Set the infinite-layer case if `IL=true` (or `μ=Inf`, or `ν=0`), in which case `ϵ` is the steepness parameter. Default is `false`.
  * `mesh`: the mesh of collocation points. By default, `mesh = Mesh(param)`;
  * `ktol`: tolerance of the low-pass Krasny filter (default is `0`, i.e. no filtering);
  * `dealias`: dealiasing with Orlicz rule `1-dealias/(dealias+2)` (default is `0`, i.e. no dealiasing);
  * `label`: a label for future references (default is `"modified Matsuno"`);

# Return values

Generate necessary ingredients for solving an initial-value problem via `solve!`:

1. a function `modifiedMatsuno.f!` to be called in explicit time-integration solvers;
2. a function `modifiedMatsuno.mapto` which from `(η,v)` of type `InitialData` provides the raw data matrix on which computations are to be executed;
3. a function `modifiedMatsuno.mapfro` which from such data matrix returns the Tuple of real vectors `(η,v,x)`, where

      * `η` is the values of surface deformation at collocation points `x`;
      * `v` is the derivative of the trace of the velocity potential at `x`.

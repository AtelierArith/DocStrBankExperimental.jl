```
WWn(param;kwargs)
```

Define an object of type `AbstractModel` in view of solving the initial-value problem for the water waves expansion proposed by [Dommermuth and Yue](https://doi.org/10.1017/s002211208700288x), [West et al.](https://doi.org/10.1029/jc092ic11p11803), [Craig and Sulem](https://doi.org/10.1006/jcph.1993.1164) (see also the account by [Choi](http://hdl.handle.net/2433/251940)) with the "rectification" method proposed by [Duchêne and Melinand](https://arxiv.org/abs/2203.03277).

# Argument

`param` is of type `NamedTuple` and must contain

  * dimensionless parameters `ϵ` (nonlinearity) and `μ` (dispersion);
  * optionally, `ν` the shallow/deep water scaling factor. By default, `ν=1` if `μ≦1` and `ν=1/√μ` otherwise. Set the infinite-layer case if `ν=0`, or `μ=Inf`.
  * numerical parameters to construct the mesh of collocation points, if `mesh` is not provided as a keyword argument.

## Optional keyword arguments

  * `IL`: Set the infinite-layer case if `IL=true` (or `μ=Inf`, or `ν=0`), in which case `ϵ` is the steepness parameter. Default is `false`.
  * `n :: Int`: the order of the expansion; linear system if `1`, quadratic if `2`, cubic if `3`, quartic if `4` (default and other values yield `2`);
  * `δ` and `m`: parameters of the rectifier operator, set as `k->min(1,|δ*k|^m)` or `k->min(1,|δ*k|^m[1]*exp(1-|δ*k|^m[2]))` if `m` is a couple

(by default is `δ=0`, i.e. no regularization and `m=-1`. Notice `m=-Inf` and `δ>0` yields a cut-off filter);

  * `mesh`: the mesh of collocation points. By default, `mesh = Mesh(param)`;
  * `ktol`: tolerance of the low-pass Krasny filter (default is `0`, i.e. no filtering);
  * `dealias`: dealiasing with Orlicz rule `1-dealias/(dealias+2)` (default is `0`, i.e. no dealiasing);
  * `label`: a label for future references (default is `"WWn"` with `n` the order of the expansion);

# Return values

Generate necessary ingredients for solving an initial-value problem via `solve!`:

1. a function `WWn.f!` to be called in explicit time-integration solvers (also `WWn.f1!` and `WWn.f2!` for the symplectic Euler solver);
2. a function `WWn.mapto` which from `(η,v)` of type `InitialData` provides the raw data matrix on which computations are to be executed;
3. a function `WWn.mapfro` which from such data matrix returns the Tuple of real vectors `(η,v,x)`, where

```
- `η` is the values of surface deformation at collocation points `x`;
- `v` is the derivative of the trace of the velocity potential at `x`.
```

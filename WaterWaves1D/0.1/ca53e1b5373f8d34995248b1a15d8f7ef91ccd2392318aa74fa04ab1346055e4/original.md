```
Airy(param;mesh,label)
```

Define an object of type `AbstractModel` in view of solving the initial-value problem for the linear ([Airy](https://en.wikipedia.org/wiki/Airy_wave_theory)) water waves equations.

# Arguments

  * `param::NamedTuple` must contain

      * the shallowness parameter `μ` (set the infinite-layer case if `μ=Inf`);
      * optionally, `ν` the shallow/deep water scaling factor. By default, `ν=1` if `μ≦1` and `ν=1/√μ` otherwise;
      * numerical parameters to construct the mesh of collocation points, if `mesh` is not provided.
  * `mesh  :: Mesh`: the mesh of collocation points. By default, `mesh = Mesh(param)`.
  * `label :: String`: a label for future references (default is `"linear (Airy)"`).

# Return values

Generate necessary ingredients for solving an initial-value problem via `solve!`:

1. a function `Airy.f!` to be called in explicit time-integration solvers;
2. a function `Airy.mapto` which from `(η,v)` of type `InitialData` provides the raw data matrix on which computations are to be executed;
3. a function `Airy.mapfro` which from such data matrix returns the Tuple of real vectors `(η,v,x)`, where

      * `η` is the values of surface deformation at collocation points `x`;
      * `v` is the derivative of the trace of the velocity potential at `x`.

Runs the `VIDA` algorithm to find the optimal template defined by the problem `prob`. The optimization will be run using the `Optimization.jl` `optimizer`. You can optionally pass a random number generator used to specify the initial points or can explicitly pass the initial location of the optimization using `init_params`. By default `vida` first transforms the parameter space to the unit hypercube. If you do not wish to do this set `unit_cube = false`.

The remaining `kwargs...` are forwarded to the `Optimization.solve` function.

!!! warn
    To use this function a user must first load Optimization, i.e. `using Optimization`


## Arguments

  * `prob`: Defines the problem you wish to solve.
  * `optimizer`: Specifies the optimizer you want to use. Any optimizer from `Optimization.jl` works.

## Optional Keyword arguments

  * `rng`: Specifies the random number generator you want to use to select the initial points.        Note that is not forwarded to the optimizers since not all can use a specific rng.
  * `init_params`: Specify the initial point of the optimization routine. The default `nothing`                will randomly draw a starting point from the parameter space
  * `unit_cube`: If true the parameters are first transformed to the unit hypercube. If false              they are transformed to ℝⁿ using `TransformVariables`
  * `kwargs...`: Additional options to be passed to the `solve` function from `Optimization.jl`

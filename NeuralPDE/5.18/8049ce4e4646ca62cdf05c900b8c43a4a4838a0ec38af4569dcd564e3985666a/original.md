```
NNDAE(chain, opt, init_params = nothing; autodiff = false, kwargs...)
```

Algorithm for solving differential algebraic equationsusing a neural network. This is a specialization of the physics-informed neural network which is used as a solver for a standard `DAEProblem`.

!!! warning
    Note that NNDAE only supports DAEs which are written in the out-of-place form, i.e. `du = f(du,u,p,t)`, and not `f(out,du,u,p,t)`. If not declared out-of-place, then the NNDAE will exit with an error.


## Positional Arguments

  * `chain`: A neural network architecture, defined as either a `Flux.Chain` or a `Lux.AbstractLuxLayer`.
  * `opt`: The optimizer to train the neural network.
  * `init_params`: The initial parameter of the neural network. By default, this is `nothing` which thus uses the random initialization provided by the neural network library.

## Keyword Arguments

  * `autodiff`: The switch between automatic (not supported yet) and numerical differentiation             for the PDE operators. The reverse mode of the loss function is always             automatic differentiation (via Zygote), this is only for the derivative             in the loss function (the derivative with respect to time).
  * `strategy`: The training strategy used to choose the points for the evaluations.             By default, `GridTraining` is used with `dt` if given.

```
invert(measured, rec0, forward; <keyword arguments>)
```

Tries to invert the `forward` model. `forward` is a function taking  an input with the shape of `rec0` and returns an object which has the  same shape as `measured`

Multiple keyword arguments can be specified for different loss functions, regularizers and mappings.

# Arguments

  * `loss=Poisson()`: the loss function being compatible to compare with `measured`.
  * `regularizer=nothing`: A regularizer function, same form as `loss`.
  * `λ=0.05`: A float indicating the total weighting of the regularizer with    respect to the global loss function
  * `mapping=Non_negative()`: Applies a mapping of the optimizer weight. Default is a              parabola which achieves a non-negativity constraint.
  * `iterations=nothing`: Specifies a number of iterations after the optimization.   definitely should stop. Will be overwritten if `opt_options` is provided. Default: 20
  * `opt_package=Opt_Optim`: decides which backend for the optimizer is used.
  * `opt=LBFGS()`: The chosen optimizer which must fit to `opt_package`.
  * `opt_options=nothing`: Can be a options file required by Optim.jl. Will overwrite iterations.
  * `debug_f=nothing`: A debug function which must take a single argument, the current reconstruction.

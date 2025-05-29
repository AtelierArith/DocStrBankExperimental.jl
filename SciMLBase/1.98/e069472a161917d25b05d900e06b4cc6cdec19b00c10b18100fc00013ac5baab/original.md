```julia
solve(prob::OptimizationProblem, alg::AbstractOptimizationAlgorithm, args...; kwargs...)
```

## Keyword Arguments

The arguments to `solve` are common across all of the optimizers. These common arguments are:

  * `maxiters` (the maximum number of iterations)
  * `maxtime` (the maximum of time the optimization runs for)
  * `abstol` (absolute tolerance in changes of the objective value)
  * `reltol` (relative tolerance  in changes of the objective value)
  * `callback` (a callback function)

If the chosen global optimizer employs a local optimization method, a similar set of common local optimizer arguments exists. The common local optimizer arguments are:

  * `local_method` (optimizer used for local optimization in global method)
  * `local_maxiters` (the maximum number of iterations)
  * `local_maxtime` (the maximum of time the optimization runs for)
  * `local_abstol` (absolute tolerance in changes of the objective value)
  * `local_reltol` (relative tolerance  in changes of the objective value)
  * `local_options` (NamedTuple of keyword arguments for local optimizer)

Some optimizer algorithms have special keyword arguments documented in the solver portion of the documentation and their respective documentation. These arguments can be passed as `kwargs...` to `solve`. Similarly, the special keyword arguments for the `local_method` of a global optimizer are passed as a `NamedTuple` to `local_options`.

Over time, we hope to cover more of these keyword arguments under the common interface.

If a common argument is not implemented for a optimizer, a warning will be shown.

## Callback Functions

The callback function `callback` is a function which is called after every optimizer step. Its signature is:

```julia
callback = (params, loss_val, other_args) -> false
```

where `params` and `loss_val` are the current parameters and loss/objective value  in the optimization loop and `other_args` are the extra return arguments of  the optimization `f`. This allows for saving values from the optimization and  using them for plotting and display without recalculating. The callback should  return a Boolean value, and the default should be `false`, such that the optimization gets stopped if it returns `true`.

### Callback Example

```julia
function loss(p)
    # Some calculations
    lossval,x,y,z
end

function callback(p,lossval,x,y,z)
    # Do some analysis

    # When lossval < 0.01, stop the optimization
    lossval < 0.01
end
```

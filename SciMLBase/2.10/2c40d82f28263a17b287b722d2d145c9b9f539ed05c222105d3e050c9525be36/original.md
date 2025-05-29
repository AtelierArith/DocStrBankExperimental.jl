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
callback = (u, loss_val, other_args) -> false
```

where `u` and `loss_val` are the current optimization variables and loss/objective value in the optimization loop and `other_args` can be the extra things returned from the optimization `f`. This allows for saving values from the optimization and using them for plotting and display without recalculating. The callback should return a Boolean value, and the default should be `false`, such that the optimization gets stopped if it returns `true`.

### Callback Example

Here we show an example a callback function that plots the prediction at the current value of the optimization variables. The loss function here returns the loss and the prediction i.e. the solution of the `ODEProblem` `prob`, so we can use the prediction in the callback.

```julia
function predict(u)
    Array(solve(prob, Tsit5(), p = u))
end

function loss(u, p)
    pred = predict(u)
    sum(abs2, batch .- pred), pred
end

callback = function (p, l, pred; doplot = false) #callback function to observe training
    display(l)
    # plot current prediction against data
    if doplot
        pl = scatter(t, ode_data[1, :], label = "data")
        scatter!(pl, t, pred[1, :], label = "prediction")
        display(plot(pl))
    end
    return false
end
```

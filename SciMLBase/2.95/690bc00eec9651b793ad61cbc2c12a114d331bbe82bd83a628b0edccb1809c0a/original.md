```julia
solve(prob::OptimizationProblem, alg::AbstractOptimizationAlgorithm, args...; kwargs...)
```

## Keyword Arguments

The arguments to `solve` are common across all of the optimizers. These common arguments are:

  * `maxiters`: the maximum number of iterations
  * `maxtime`: the maximum amount of time (typically in seconds) the optimization runs for
  * `abstol`: absolute tolerance in changes of the objective value
  * `reltol`: relative tolerance  in changes of the objective value
  * `callback`: a callback function

Some optimizer algorithms have special keyword arguments documented in the solver portion of the documentation and their respective documentation. These arguments can be passed as `kwargs...` to `solve`. Similarly, the special keyword arguments for the `local_method` of a global optimizer are passed as a `NamedTuple` to `local_options`.

Over time, we hope to cover more of these keyword arguments under the common interface.

A warning will be shown if a common argument is not implemented for an optimizer.

## Callback Functions

The callback function `callback` is a function that is called after every optimizer step. Its signature is:

```julia
callback = (state, loss_val) -> false
```

where `state` is an `OptimizationState` and stores information for the current iteration of the solver and `loss_val` is loss/objective value. For more information about the fields of the `state` look at the `OptimizationState` documentation. The callback should return a Boolean value, and the default should be `false`, so the optimization stops if it returns `true`.

### Callback Example

Here we show an example of a callback function that plots the prediction at the current value of the optimization variables. For a visualization callback, we would need the prediction at the current parameters i.e. the solution of the `ODEProblem` `prob`. So we call the `predict` function within the callback again.

```julia
function predict(u)
    Array(solve(prob, Tsit5(), p = u))
end

function loss(u, p)
    pred = predict(u)
    sum(abs2, batch .- pred)
end

callback = function (state, l; doplot = false) #callback function to observe training
    display(l)
    # plot current prediction against data
    if doplot
        pred = predict(state.u)
        pl = scatter(t, ode_data[1, :], label = "data")
        scatter!(pl, t, pred[1, :], label = "prediction")
        display(plot(pl))
    end
    return false
end
```

If the chosen method is a global optimizer that employs a local optimization method, a similar set of common local optimizer arguments exists. Look at `MLSL` or `AUGLAG` from NLopt for an example. The common local optimizer arguments are:

  * `local_method`: optimizer used for local optimization in global method
  * `local_maxiters`: the maximum number of iterations
  * `local_maxtime`: the maximum amount of time (in seconds) the optimization runs for
  * `local_abstol`: absolute tolerance in changes of the objective value
  * `local_reltol`: relative tolerance  in changes of the objective value
  * `local_options`: `NamedTuple` of keyword arguments for local optimizer

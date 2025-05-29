```
curve = learning_curve(mach; resolution=30,
                             resampling=Holdout(),
                             repeats=1,
                             measure=default_measure(machine.model),
                             rows=nothing,
                             weights=nothing,
                             operation=nothing,
                             range=nothing,
                             acceleration=default_resource(),
                             acceleration_grid=CPU1(),
                             rngs=nothing,
                             rng_name=nothing)
```

Given a supervised machine `mach`, returns a named tuple of objects suitable for generating a plot of performance estimates, as a function of the single hyperparameter specified in `range`. The tuple `curve` has the following keys: `:parameter_name`, `:parameter_scale`, `:parameter_values`, `:measurements`.

To generate multiple curves for a `model` with a random number generator (RNG) as a hyperparameter, specify the name, `rng_name`, of the (possibly nested) RNG field, and a vector `rngs` of RNG's, one for each curve. Alternatively, set `rngs` to the number of curves desired, in which case RNG's are automatically generated. The individual curve computations can be distributed across multiple processes using `acceleration=CPUProcesses()` or `acceleration=CPUThreads()`. See the second example below for a demonstration.

```julia
X, y = @load_boston;
atom = @load RidgeRegressor pkg=MultivariateStats
ensemble = EnsembleModel(atom=atom, n=1000)
mach = machine(ensemble, X, y)
r_lambda = range(ensemble, :(atom.lambda), lower=10, upper=500, scale=:log10)
curve = learning_curve(mach; range=r_lambda, resampling=CV(), measure=mav)
using Plots
plot(curve.parameter_values,
     curve.measurements,
     xlab=curve.parameter_name,
     xscale=curve.parameter_scale,
     ylab = "CV estimate of RMS error")
```

If using a `Holdout()` `resampling` strategy (with no shuffling) and if the specified hyperparameter is the number of iterations in some iterative model (and that model has an appropriately overloaded `MLJModelInterface.update` method) then training is not restarted from scratch for each increment of the parameter, ie the model is trained progressively.

```julia
atom.lambda=200
r_n = range(ensemble, :n, lower=1, upper=250)
curves = learning_curve(mach; range=r_n, verbosity=0, rng_name=:rng, rngs=3)
plot!(curves.parameter_values,
     curves.measurements,
     xlab=curves.parameter_name,
     ylab="Holdout estimate of RMS error")


```

```
learning_curve(model::Supervised, X, y; kwargs...)
learning_curve(model::Supervised, X, y, w; kwargs...)
```

Plot a learning curve (or curves) directly, without first constructing a machine.

### Summary of key-word options

  * `resolution` - number of points generated from `range` (number model evaluations); default is `30`
  * `acceleration` - parallelization option for passing to `evaluate!`; an instance of `CPU1`, `CPUProcesses` or `CPUThreads` from the `ComputationalResources.jl`; default is `default_resource()`
  * `acceleration_grid` - parallelization option for distributing each performancde evaluation
  * `rngs` - for specifying random number generator(s) to be passed to the model (see above)
  * `rng_name` - name of the model hyper-parameter representing a random number generator (see above); possibly nested

Other key-word options are documented at [`TunedModel`](@ref).

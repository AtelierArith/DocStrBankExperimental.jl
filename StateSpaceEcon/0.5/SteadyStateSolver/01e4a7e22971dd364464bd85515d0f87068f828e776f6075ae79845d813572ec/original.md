```
initial_sstate!(model, init; <options>)
```

Set the steady state values from the given vector and presolve.

Call this function to specify initial guesses for the iterative steady state solver. If the value of a steady state variable is known, it is better to use [`@steadystate`](@ref ModelBaseEcon.@steadystate) to add that as a steady state constraint.

### Arguments

  * `model` - the model.
  * `init` - a vector of length equal to twice the number of variables in the model. The level and slope values are staggered, i.e., the level and slope of variable j are in init[2j-1] and init[2j].

### Options

Standard options (default values are taken from `model.options`)

  * `verbose`

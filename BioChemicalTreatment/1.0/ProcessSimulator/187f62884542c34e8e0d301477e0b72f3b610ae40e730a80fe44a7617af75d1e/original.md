```
Process
```

An implementation of [`AbstractProcessElement`](@ref) for processes used to  compute and provide the reaction rates to reactors.

# Constructors

```
Process(args...; name, error_invalid_composition=true, kwargs...)
```

Loads a process from files over the `BioChemicalReactionSystem`. Generates the process and checks if the composition requirement is fulfilled.

## Arguments

  * `args...`: The arguments to pass on to the [`Reactions.BioChemicalReactionSystem`](@ref). See docs there for possiblities.

## Keyword Arguments

  * `name`: The name of the created system
  * `error_invalid_composition`: If an error should be thrown on invalid compositions. Defaults to true to force the user   to actively activate that the invalid composition works. A warning is thrown instead of an error if this argument is   set to `false`
  * `kwargs...`: Keyword arguments specifying the parameters of the model. An error is thrown if no matching parameter is found to set.    Can be values or expressions of the other parameters.

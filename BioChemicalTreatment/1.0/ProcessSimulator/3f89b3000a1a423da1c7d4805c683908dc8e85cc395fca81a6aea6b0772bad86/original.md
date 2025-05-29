```
sates(sys)
```

Get the states connector of the dynamical system represented by the process element `sys`.

This function returns the states of the dynamical system, i.e. all variables that  are involved as derivatives in any of the differential equations describing the model. As not all systems are dynamic (they can be static as well), this function is not applicable to static systems. Additionally this connector is used for all process elements which need the internal states of a dynamical systems for processing, i.e. the [`Process`](@ref) need the states of the associated [`Reactor`](@ref) to compute the rates.

# Extended Help

# Implementation

This function should be overridden for each type inheriting from [`AbstractProcessElement`](@ref) which has states or needs the states of another [`AbstractProcessElement`](@ref). Note that depending on if it needs or provides states, different connectors are needed ([`StateInputPort`](@ref) vs. [`StateOutputPort`](@ref))

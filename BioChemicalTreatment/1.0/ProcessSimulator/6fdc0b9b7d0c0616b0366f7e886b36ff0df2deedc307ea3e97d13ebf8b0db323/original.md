```
rates(sys)
```

Get the rates connector of the system represented by the process element `sys`.

This function returns the rates of the system. Not all process elements have rates, but this mainly used for [`Reactor`](@ref)s and [`Process`](@ref)es. The [`Reactor`](@ref) uses the rates as reaction rates for the process happening in the [`Reactor`](@ref) and the [`Process`](@ref) provides these rates to the reactor.

# Extended Help

# Implementation

This function should be overridden for each type inheriting from [`AbstractProcessElement`](@ref) which needs or provides rates. Note that depending on if it needs or provides rates, different  connectors are needed ([`ReactionInputPort`](@ref) vs. [`ReactionOutputPort`](@ref))

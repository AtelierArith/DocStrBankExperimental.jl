A collection of `Advices` sourced from available Plugins.

Like individual `Advices`, a `AdviceAmalgamation` can be called as a function. However, it also supports the following convenience syntax:

```
(::AdviceAmalgamation)(f::Function, args...; kargs...) # -> result
```

# Constructors

```
AdviceAmalgamation(adviseall::Function, advisors::Vector{Advice},
                   plugins_wanted::Vector{String}, plugins_used::Vector{String})
AdviceAmalgamation(plugins::Vector{String})
AdviceAmalgamation(collection::DataCollection)
```

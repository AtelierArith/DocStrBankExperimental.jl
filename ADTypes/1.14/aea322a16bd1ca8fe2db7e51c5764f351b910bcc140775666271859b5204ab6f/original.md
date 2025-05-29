```
AutoTapir
```

!!! danger
    `AutoTapir` is deprecated following a package renaming, please use [`AutoMooncake`](@ref) instead.


Struct used to select the [Tapir.jl](https://github.com/compintell/Tapir.jl) backend for automatic differentiation.

Defined by [ADTypes.jl](https://github.com/SciML/ADTypes.jl).

# Constructors

```
AutoTapir(; safe_mode=true)
```

# Fields

  * `safe_mode::Bool`: whether to run additional checks to catch errors early.

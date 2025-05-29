```
AutoMooncake
```

Struct used to select the [Mooncake.jl](https://github.com/compintell/Mooncake.jl) backend for automatic differentiation.

Defined by [ADTypes.jl](https://github.com/SciML/ADTypes.jl).

# Constructors

```
AutoMooncake(; config)
```

# Fields

  * `config`: either `nothing` or an instance of `Mooncake.Config` – see the docstring of `Mooncake.Config` for more information. `AutoMooncake(; config=nothing)` is equivalent to `AutoMooncake(; config=Mooncake.Config())`, i.e. the default configuration.

```
AutoTaylorDiff{order}
```

Struct used to select the [TaylorDiff.jl](https://github.com/JuliaDiff/TaylorDiff.jl) backend for automatic differentiation.

Defined by [ADTypes.jl](https://github.com/SciML/ADTypes.jl).

# Constructors

```
AutoTaylorDiff(; order = 1)
```

# Type parameters

  * `order`: the order of the Taylor-mode automatic differentiation

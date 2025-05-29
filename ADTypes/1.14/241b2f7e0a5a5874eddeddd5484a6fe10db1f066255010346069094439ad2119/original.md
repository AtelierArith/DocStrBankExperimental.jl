```
AutoFiniteDifferences{T}
```

Struct used to select the [FiniteDifferences.jl](https://github.com/JuliaDiff/FiniteDifferences.jl) backend for automatic differentiation.

Defined by [ADTypes.jl](https://github.com/SciML/ADTypes.jl).

# Constructors

```
AutoFiniteDifferences(; fdm)
```

# Fields

  * `fdm::T`: a [`FiniteDifferenceMethod`](https://juliadiff.org/FiniteDifferences.jl/stable/pages/api/#FiniteDifferences.FiniteDifferenceMethod)

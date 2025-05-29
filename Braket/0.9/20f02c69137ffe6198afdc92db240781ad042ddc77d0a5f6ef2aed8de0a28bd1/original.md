```
FreeParameter
FreeParameter(name::Symbol) -> FreeParameter
```

Struct representing a free parameter, which may be used to initialize to a parametrized [`Gate`](@ref) or [`Noise`](@ref) and then given a fixed value later by supplying a mapping to a [`Circuit`](@ref).

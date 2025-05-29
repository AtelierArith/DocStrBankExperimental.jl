```
Selector
```

Abstract supertype for all selectors.

Selectors are wrappers that indicate that passed values are not the array indices, but values to be selected from the dimension index, such as `DateTime` objects for a `Ti` dimension.

Selectors provided in DimensionalData are:

  * [`At`](@ref)
  * [`Between`](@ref)
  * [`Touches`](@ref)
  * [`Near`](@ref)
  * [`Where`](@ref)
  * [`Contains`](@ref)

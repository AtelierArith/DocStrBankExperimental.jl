```
abstract type AbstractLuxWrapperLayer{layer} <: AbstractLuxLayer
```

See [`AbstractLuxContainerLayer`](@ref) for detailed documentation. This abstract type is very similar to [`AbstractLuxContainerLayer`](@ref) except that it allows for a single layer to be wrapped in a container.

Additionally, on calling [`initialparameters`](@ref) and [`initialstates`](@ref), the parameters and states are **not** wrapped in a `NamedTuple` with the same name as the field.

As a convenience, we define the fallback call `(::AbstractLuxWrapperLayer)(x, ps, st)`, which calls `getfield(x, layer)(x, ps, st)`.

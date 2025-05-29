```
abstract type AbstractLuxContainerLayer{layers} <: AbstractLuxLayer
```

Abstract Container Type for certain Lux Layers. `layers` is a tuple containing fieldnames for the layer, and constructs the parameters and states using those.

Users implementing their custom layer can extend the same functions as in [`AbstractLuxLayer`](@ref).

!!! tip "Advanced Structure Manipulation"
    Advanced structure manipulation of these layers post construction is possible via `Functors.fmap`. For a more flexible interface, we recommend using `Lux.Experimental.@layer_map`.


!!! note "`fmap` Support"
    `fmap` support needs to be explicitly enabled by loading `Functors.jl` and `Setfield.jl`.


!!! warning "Changes from Pre-1.0 Behavior"
    Previously if `layers` was a singleton tuple, [`initialparameters`](@ref) and [`initialstates`](@ref) would return the parameters and states for the single field `layers`. From `v1.0.0` onwards, even for singleton tuples, the parameters/states are wrapped in a `NamedTuple` with the same name as the field. See [`AbstractLuxWrapperLayer`](@ref) to replicate the previous behavior of singleton tuples.


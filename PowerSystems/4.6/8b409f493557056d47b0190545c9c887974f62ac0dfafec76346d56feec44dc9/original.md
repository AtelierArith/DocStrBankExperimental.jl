Abstract type for devices that [inject](@ref I) power or current

A [static](@ref S) injection is a steady state injection, such as modeling the output power of a generator held constant over a five-minute period.

Many `StaticInjection` models can accept a [`DynamicInjection`](@ref) model as an optional add-on for conducting [dynamic](@ref D) simulations.

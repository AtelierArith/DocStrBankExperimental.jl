```julia
couple(systems...) -> EarthSciMLBase.CoupledSystem

```

Couple multiple ModelingToolkit systems together.

The systems that are arguments to this system can be of type `ModelingToolkit.AbstractSystem`, [`CoupledSystem`](@ref), [`DomainInfo`](@ref), or any type `T` that has a method `couple(::CoupledSystem, ::T)::CoupledSystem` or a method `couple(::T, ::CoupledSystem)::CoupledSystem` defined for it.

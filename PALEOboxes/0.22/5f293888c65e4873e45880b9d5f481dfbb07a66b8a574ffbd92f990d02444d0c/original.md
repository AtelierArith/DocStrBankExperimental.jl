```
AbstractReaction
```

Abstract base Type for Reactions.

# Implementation

Derived types should include a field `base::`[`ReactionBase`](@ref), and usually a [`ParametersTuple`](@ref), eg

```
Base.@kwdef mutable struct ReactionHello{P} <: PB.AbstractReaction
    base::PB.ReactionBase

    pars::P = PB.ParametersTuple(
        PB.ParDouble("my_par", 42.0, units="yr", 
            description="an example of a Float64-valued scalar parameter called 'my_par'"),
    )

    some_additional_field::Float64   # additional fields to eg cache data read from disk etc
end
```

Derived types should implement [`register_methods!`](@ref), and may optionally implement [`create_reaction`](@ref),  [`set_model_geometry`](@ref), [`check_configuration`](@ref), [`register_dynamic_methods!`](@ref).

Methods should be registered using [`add_method_setup!`](@ref), [`add_method_initialize!`](@ref), [`add_method_do!`](@ref).

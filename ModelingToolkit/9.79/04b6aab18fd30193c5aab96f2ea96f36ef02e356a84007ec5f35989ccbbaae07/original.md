```julia
extend(
    sys::ModelingToolkit.AbstractSystem,
    basesys::ModelingToolkit.AbstractSystem;
    name,
    description,
    gui_metadata
) -> Catalyst.ReactionSystem{Catalyst.NetworkProperties{Int64, V}} where V<:SymbolicUtils.BasicSymbolic{Real}

```

Extend `basesys` with `sys`. By default, the resulting system inherits `sys`'s name and description.

See also [`compose`](@ref).

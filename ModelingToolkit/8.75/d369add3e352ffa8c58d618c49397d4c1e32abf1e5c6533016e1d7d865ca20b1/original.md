```julia
extend(
    sys::ModelingToolkit.AbstractSystem,
    basesys::ModelingToolkit.AbstractSystem;
    name,
    gui_metadata
) -> Catalyst.ReactionSystem{Catalyst.NetworkProperties{Int64, V}} where V<:SymbolicUtils.BasicSymbolic{Real}

```

extend the `basesys` with `sys`, the resulting system would inherit `sys`'s name by default.

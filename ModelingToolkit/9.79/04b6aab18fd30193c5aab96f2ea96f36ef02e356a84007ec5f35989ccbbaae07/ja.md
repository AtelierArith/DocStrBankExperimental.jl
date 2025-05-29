```julia
extend(
    sys::ModelingToolkit.AbstractSystem,
    basesys::ModelingToolkit.AbstractSystem;
    name,
    description,
    gui_metadata
) -> Catalyst.ReactionSystem{Catalyst.NetworkProperties{Int64, V}} where V<:SymbolicUtils.BasicSymbolic{Real}

```

`basesys`を`sys`で拡張します。デフォルトでは、結果のシステムは`sys`の名前と説明を継承します。

[`compose`](@ref)も参照してください。

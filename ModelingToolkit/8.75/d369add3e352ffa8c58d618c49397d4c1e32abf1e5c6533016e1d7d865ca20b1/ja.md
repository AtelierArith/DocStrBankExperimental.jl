```julia
extend(
    sys::ModelingToolkit.AbstractSystem,
    basesys::ModelingToolkit.AbstractSystem;
    name,
    gui_metadata
) -> Catalyst.ReactionSystem{Catalyst.NetworkProperties{Int64, V}} where V<:SymbolicUtils.BasicSymbolic{Real}

```

`basesys`を`sys`で拡張すると、結果のシステムはデフォルトで`sys`の名前を継承します。

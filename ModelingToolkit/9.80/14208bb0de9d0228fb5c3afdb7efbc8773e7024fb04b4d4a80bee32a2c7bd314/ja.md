```julia
extend(
    sys::ModelingToolkit.AbstractSystem,
    basesys::ModelingToolkit.AbstractSystem;
    name,
    description,
    gui_metadata
) -> Any

```

`basesys`を`sys`で拡張します。デフォルトでは、結果のシステムは`sys`の名前と説明を継承します。

関連情報は[`compose`](@ref)を参照してください。

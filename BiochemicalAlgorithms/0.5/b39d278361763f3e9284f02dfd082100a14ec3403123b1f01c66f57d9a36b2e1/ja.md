```julia
secondary_structure_by_idx(
    sys::BiochemicalAlgorithms.System{T},
    idx::Int64
) -> BiochemicalAlgorithms.SecondaryStructure

```

指定された `idx` に関連付けられた `SecondaryStructure{T}` を `sys` から返します。該当する二次構造が存在しない場合は `KeyError` をスローします。

```
chain_by_idx(
    sys::System{T} = default_system(),
    idx::Int
) -> Chain{T}
```

指定された `idx` に関連付けられた `Chain{T}` を `sys` から返します。該当するチェーンが存在しない場合は `KeyError` をスローします。

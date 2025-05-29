```
bond_by_idx(
    sys::System{T} = default_system(),
    idx::Int
) -> Bond{T}
```

指定された `idx` に関連付けられた `Bond{T}` を `sys` から返します。該当するボンドが存在しない場合は `KeyError` をスローします。

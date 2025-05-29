```
fragment_by_idx(
    sys::System{T} = default_system(),
    idx::Int
) -> Fragment{T}
```

指定された `idx` に関連付けられた `Fragment{T}` を `sys` から返します。該当するフラグメントが存在しない場合は `KeyError` をスローします。

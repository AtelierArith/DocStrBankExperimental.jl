```
atom_by_idx(
    sys::System{T} = default_system(),
    idx::Int
) -> Atom{T}
```

指定された `idx` に関連付けられた `Atom{T}` を `sys` から返します。該当する原子が存在しない場合は `KeyError` をスローします。

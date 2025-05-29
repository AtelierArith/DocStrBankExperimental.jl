```
delete_default!(c::ComponentModel, sym::Symbol)
delete_default!(nw::Network, sni::SymbolicIndex)
```

コンポーネントモデル内のシンボル `sym` に対する `default` 値を削除するか、ネットワーク内の `sni` に参照されるシンボルに対する `default` 値を削除します。

関連情報として [`has_default`](@ref)、[`set_default!`](@ref) を参照してください。

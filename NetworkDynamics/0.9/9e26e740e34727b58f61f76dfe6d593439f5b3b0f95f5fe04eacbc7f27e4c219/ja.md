```
delete_bounds!(c::ComponentModel, sym::Symbol)
delete_bounds!(nw::Network, sni::SymbolicIndex)
```

コンポーネントモデル内のシンボル `sym` に対する `bounds` 値を削除するか、ネットワーク内の `sni` に参照されるシンボルに対する `bounds` 値を削除します。

関連情報として [`has_bounds`](@ref)、[`set_bounds!`](@ref) を参照してください。

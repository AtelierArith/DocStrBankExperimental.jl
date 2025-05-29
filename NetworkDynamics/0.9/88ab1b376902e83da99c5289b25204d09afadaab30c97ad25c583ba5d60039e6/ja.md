```
delete_guess!(c::ComponentModel, sym::Symbol)
delete_guess!(nw::Network, sni::SymbolicIndex)
```

コンポーネントモデル内のシンボル `sym` に対する `guess` 値を削除するか、ネットワーク内の `sni` に参照されるシンボルに対する `guess` 値を削除します。

関連情報としては [`has_guess`](@ref)、[`set_guess!`](@ref) を参照してください。

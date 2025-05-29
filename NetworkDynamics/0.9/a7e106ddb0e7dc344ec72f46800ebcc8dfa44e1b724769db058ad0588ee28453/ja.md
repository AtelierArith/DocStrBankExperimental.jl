```
delete_init!(c::ComponentModel, sym::Symbol)
delete_init!(nw::Network, sni::SymbolicIndex)
```

コンポーネントモデル内のシンボル `sym` に対する `init` 値を削除するか、ネットワーク内の `sni` に参照されるシンボルに対する `init` 値を削除します。

関連情報としては [`has_init`](@ref)、[`set_init!`](@ref) があります。

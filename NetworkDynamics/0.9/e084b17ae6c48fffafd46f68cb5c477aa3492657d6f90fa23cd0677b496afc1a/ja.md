```
get_default(c::ComponentModel, sym::Symbol)
get_default(nw::Network, sni::SymbolicIndex)
```

コンポーネントモデル内のシンボル `sym` に対する `default` 値、またはネットワーク内の `sni` によって参照されるシンボルに対する `default` 値を返します。

関連情報として [`has_default`](@ref)、[`set_default!`](@ref) を参照してください。

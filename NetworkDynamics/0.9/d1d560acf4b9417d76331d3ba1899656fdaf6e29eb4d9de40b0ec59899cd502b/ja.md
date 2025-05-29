```
get_init(c::ComponentModel, sym::Symbol)
get_init(nw::Network, sni::SymbolicIndex)
```

コンポーネントモデル内のシンボル `sym` に対する `init` 値、またはネットワーク内の `sni` によって参照されるシンボルに対する `init` 値を返します。

関連情報として [`has_init`](@ref)、[`set_init!`](@ref) を参照してください。

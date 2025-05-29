```
get_bounds(c::ComponentModel, sym::Symbol)
get_bounds(nw::Network, sni::SymbolicIndex)
```

コンポーネントモデル内のシンボル `sym` に対する `bounds` 値、またはネットワーク内の `sni` によって参照されるシンボルに対する `bounds` 値を返します。

関連情報として [`has_bounds`](@ref)、[`set_bounds!`](@ref) を参照してください。

```
has_bounds(c::ComponentModel, sym::Symbol)
has_bounds(nw::Network, sni::SymbolicIndex)
```

コンポーネントモデル内のシンボル `sym` に対して `bounds` 値が存在するか、またはネットワーク内の `sni` に参照されるシンボルに対して存在するかをチェックします。

関連情報として [`get_bounds`](@ref)、[`set_bounds!`](@ref) を参照してください。

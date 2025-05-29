```
has_default(c::ComponentModel, sym::Symbol)
has_default(nw::Network, sni::SymbolicIndex)
```

コンポーネントモデル内のシンボル `sym` に対して `default` 値が存在するか、またはネットワーク内の `sni` によって参照されるシンボルに対して存在するかをチェックします。

関連情報として [`get_default`](@ref)、[`set_default!`](@ref) を参照してください。

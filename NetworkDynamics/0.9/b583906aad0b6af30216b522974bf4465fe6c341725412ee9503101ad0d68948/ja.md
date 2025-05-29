```
has_init(c::ComponentModel, sym::Symbol)
has_init(nw::Network, sni::SymbolicIndex)
```

コンポーネントモデル内のシンボル `sym` に対して `init` 値が存在するか、またはネットワーク内の `sni` に参照されるシンボルに対して存在するかをチェックします。

関連情報として [`get_init`](@ref)、[`set_init!`](@ref) を参照してください。

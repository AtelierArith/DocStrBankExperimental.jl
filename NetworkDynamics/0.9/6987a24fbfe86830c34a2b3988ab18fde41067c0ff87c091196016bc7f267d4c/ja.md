```
get_guess(c::ComponentModel, sym::Symbol)
get_guess(nw::Network, sni::SymbolicIndex)
```

コンポーネントモデル内のシンボル `sym` に対する `guess` 値、またはネットワーク内の `sni` によって参照されるシンボルに対する `guess` 値を返します。

関連情報として [`has_guess`](@ref)、[`set_guess!`](@ref) を参照してください。

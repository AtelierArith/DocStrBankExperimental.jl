```
has_guess(c::ComponentModel, sym::Symbol)
has_guess(nw::Network, sni::SymbolicIndex)
```

コンポーネントモデル内のシンボル `sym` に対して、またはネットワーク内の `sni` によって参照されるシンボルに対して `guess` 値が存在するかどうかを確認します。

関連情報として [`get_guess`](@ref)、[`set_guess!`](@ref) を参照してください。

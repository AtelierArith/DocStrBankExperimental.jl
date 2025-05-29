```
set_default!(c::ComponentModel, sym::Symbol, value)
set_default!(nw::Network, sni::SymbolicIndex, value)
```

コンポーネントモデル内のシンボル `sym` の `default` 値を `value` に設定するか、ネットワーク内の `sni` に参照されるシンボルの `default` 値を設定します。

関連情報として [`has_default`](@ref)、[`get_default`](@ref) を参照してください。

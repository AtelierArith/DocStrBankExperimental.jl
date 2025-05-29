```
set_init!(c::ComponentModel, sym::Symbol, value)
set_init!(nw::Network, sni::SymbolicIndex, value)
```

コンポーネントモデル内のシンボル `sym` の `init` 値を `value` に設定するか、ネットワーク内の `sni` に参照されるシンボルの `init` 値を設定します。

関連情報として [`has_init`](@ref)、[`get_init`](@ref) を参照してください。

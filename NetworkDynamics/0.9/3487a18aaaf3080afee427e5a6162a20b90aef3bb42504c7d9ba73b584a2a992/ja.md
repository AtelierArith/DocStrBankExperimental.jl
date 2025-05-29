```
set_bounds!(c::ComponentModel, sym::Symbol, value)
set_bounds!(nw::Network, sni::SymbolicIndex, value)
```

コンポーネントモデル内のシンボル `sym` の `bounds` 値を `value` に設定するか、ネットワーク内の `sni` に参照されるシンボルの `bounds` 値を `value` に設定します。

関連情報として [`has_bounds`](@ref)、[`get_bounds`](@ref) を参照してください。

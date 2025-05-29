```
set_guess!(c::ComponentModel, sym::Symbol, value)
set_guess!(nw::Network, sni::SymbolicIndex, value)
```

コンポーネントモデル内のシンボル `sym` の `guess` 値を `value` に設定するか、ネットワーク内の `sni` に参照されるシンボルの `guess` 値を設定します。

関連情報として [`has_guess`](@ref)、[`get_guess`](@ref) を参照してください。

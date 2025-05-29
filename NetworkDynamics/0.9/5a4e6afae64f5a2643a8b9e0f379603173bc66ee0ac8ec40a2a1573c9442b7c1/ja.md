```
set_metadata!(c::ComponentModel, sym::Symbol, key::Symbol, value)
set_metadata!(nw::Network, sni::SymbolicIndex, key::Symbol, value)
set_metadata!(c::ComponentModel, sym::Symbol, pair::Pair)
set_metadata!(nw::Network, sni::SymbolicIndex, pair::Pair)
```

コンポーネントモデル内のシンボル `sym` に対してメタデータ `key` を `value` に設定するか、ネットワーク内の `sni` で参照されるシンボルに対して設定します。シンボルがコンポーネントモデル内に存在しない場合はエラーをスローします。

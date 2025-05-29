```
get_metadata(c::ComponentModel, sym::Symbol, key::Symbol)
get_metadata(nw::Network, sni::SymbolicIndex, key::Symbol)
```

コンポーネントモデル内のシンボル `sym` に対するメタデータ `key` を取得するか、ネットワーク内の `sni` に参照されるシンボルに対するメタデータを取得します。シンボルがコンポーネントモデル内に存在しない場合はエラーをスローします。

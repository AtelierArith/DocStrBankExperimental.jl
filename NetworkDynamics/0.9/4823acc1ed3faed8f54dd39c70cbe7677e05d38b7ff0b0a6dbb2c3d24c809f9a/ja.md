```
has_metadata(c::ComponentModel, sym::Symbol, key::Symbol)
has_metadata(nw::Network, sni::SymbolicIndex, key::Symbol)
```

コンポーネントモデル内のシンボル `sym` に対して、またはネットワーク内の `sni` によって参照されるシンボルに対して、シンボルメタデータ `key` が存在するかどうかをチェックします。シンボルがコンポーネントモデルに存在しない場合はエラーをスローします。

```
delete_metadata!(c::ComponentModel, sym::Symbol, key::Symbol)
delete_metadata!(nw::Network, sni::SymbolicIndex, key::Symbol)
```

コンポーネントモデル内のシンボル `sym` に対するメタデータ `key` を削除するか、ネットワーク内の `sni` に参照されるシンボルに対するメタデータを削除します。メタデータが存在し削除された場合は `true` を返し、そうでない場合は `false` を返します。シンボルがコンポーネントモデル内に存在しない場合はエラーをスローします。

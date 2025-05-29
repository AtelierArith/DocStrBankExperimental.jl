```
delete_metadata!(c::ComponentModel, key::Symbol)
delete_metadata!(nw::Network, idx::Union{VIndex,EIndex}, key::Symbol)
```

コンポーネントモデルからコンポーネント全体のメタデータ `key` を削除するか、ネットワーク内の `idx` で参照されるコンポーネントから削除します。メタデータが存在し、削除された場合は `true` を返し、そうでない場合は `false` を返します。

```
CachedDomain(source::Domain)
CachedDomain(source::Domain, method_keys)
```

`source` ドメインから `CachedDomain` を構築し、各キャッシュされたメソッドに関連するキャッシュを含めます。キャッシュするメソッドを指定する `Symbol` のリストである `method_keys` を提供できます。

デフォルトでは、次のメソッドがキャッシュされます: `[:available, :relevant, :infer_static_fluents, :infer_affected_fluents, :infer_axiom_hierarchy]`。

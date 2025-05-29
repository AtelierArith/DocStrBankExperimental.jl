```
exp!(M::AbstractManifold, q, p, X)
```

接続体 `X` の指数写像を、マンホールド [`AbstractManifold`](@ref) `M` の点 `p` で計算します。結果は `q` に保存されます。

自分のマンホールドのために指数写像を実装したい場合は、インプレースメソッド `exp_fused!(M::MyManifold, q, p, X)` を実装する必要があります。

詳細は [`exp`](@ref) を参照してください。

```
exp!(M::AbstractManifold, q, p, X)
exp!(M::AbstractManifold, q, p, X, t::Number = 1)
```

接続されたベクトル `X` の指数写像を、マンフォールド [`AbstractManifold`](@ref) `M` の点 `p` で計算します。結果は `q` に保存されます。`t` でスケーリングすることもできます。

あなたのマンフォールドのために指数写像を実装したい場合は、`t` を持つメソッド、すなわち `exp!(M::MyManifold, q, p, X, t::Number)` を実装する必要があります。

詳細は [`exp`](@ref) を参照してください。

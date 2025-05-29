```
sample(N::T, n::Tuple{Int64}) where {T<:AbstractUnipartiteNetwork}
```

`sample`と同様ですが、種番号の代わりに`(n,)`で呼び出すと動作します。これはユニパーティネットワークをサンプリングするための受け入れられた方法です。

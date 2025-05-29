```
sample(N::T, n::Int64) where {T<:AbstractBipartiteNetwork}
```

`sample`と同じですが、単一の種数を指定して、両側で同じ豊かさの二部ネットワークを返します。これは二部ネットワークをサンプリングするためのあまり良い方法ではありません。

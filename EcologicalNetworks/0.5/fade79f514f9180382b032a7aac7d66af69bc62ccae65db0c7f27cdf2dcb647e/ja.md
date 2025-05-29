```
sample(N::T, n::Tuple{Int64}) where {T<:AbstractBipartiteNetwork}
```

`sample`と同様ですが、単一の種数が`(n,)`として与えられ、両側で同じ豊かさの二部ネットワークを返します。これは二部ネットワークをサンプリングするためのあまり良い方法ではありません。

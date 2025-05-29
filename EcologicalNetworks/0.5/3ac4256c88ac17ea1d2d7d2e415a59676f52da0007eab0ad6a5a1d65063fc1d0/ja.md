```
sample(N::T, n::Tuple{Int64,Int64}) where {T<:AbstractUnipartiteNetwork}
```

`sample`と同じですが、種の数の代わりに`(n,n)`で呼び出されます。要求されたサイズが正方形でない場合、これは失敗します。これはユニパーティネットワークをサンプリングするための本当に良い方法ではありません。

```
localfilter([T=eltype(A),] A, B, initial, update, final=identity; kwds...) -> dst
```

[`localfilter!`](@ref) の非破壊版で、次のように等価です：

```
localfilter!(similar(A, T), A, B, initial, update, final=identity; kwds...)
```

オプションの引数 `T` は結果の要素型を指定するためのもので、デフォルトでは `T` は `A` の要素型です。

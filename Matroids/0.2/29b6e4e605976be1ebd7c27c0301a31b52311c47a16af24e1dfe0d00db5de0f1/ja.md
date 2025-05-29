```
rank(M::Matroid, X::Set{T})::Int where {T<:Integer}
rank(M::Matroid)::Int
```

マトロイド `M` における集合 `X` のランクを返します。

`rank` を呼び出すための代替方法をサポートしています。例えば、`rank(M,a,b,c)` と `rank(M,[a,b,c])` は `rank(M,Set([a,b,c]))` と同じです。

`X` がない場合、マトロイド `M` のランクを返します。

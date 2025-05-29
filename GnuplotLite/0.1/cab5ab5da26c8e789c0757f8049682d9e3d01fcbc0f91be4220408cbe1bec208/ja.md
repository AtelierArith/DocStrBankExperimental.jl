```
 send(::Pair{String,Matrix{T}}) where T <: Number
```

行列をGnuplotに送信し、変数に格納します。このバリアントは、行列が均一な行列に関するGnuplotのドキュメントで説明されているように、`[0..N-1]`から整数インデックスを取得することを前提としています。

[`Msg`](@ref)を返します。

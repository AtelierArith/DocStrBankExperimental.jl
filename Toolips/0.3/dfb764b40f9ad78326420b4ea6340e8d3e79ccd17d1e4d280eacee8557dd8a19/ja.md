```julia
abstract type AbstractRoute
```

`AbstractRoute`は、ユーザーがウェブページをナビゲートするためのターゲットである`path`と、そのページを生成する方法を保持します。通常、これらは`route`を使用して作成されますが、必ずしもそうではない場合もあります。`Toolips`によって提供される標準的なルートは`Route{<:Any}`です。

  * 参照: `route`, `route!`, `Connection`, `AbstractConnection`

`expand(b::BitlyToken,link::AbstractString)`

`bit.ly/xXxXx` 短縮リンクから元の `url` を復元します。

`long_url` と `response` アイテムを持つ `NamedTuple` を返します。`long_url` は元のリンクで、`response` は Bitly API からの完全な `JSON` レスポンスです。

```julia
b = BitlyToken()
S = expand(b,"http://bit.ly/2Us5Vl7")
S.long_url
S.response
```

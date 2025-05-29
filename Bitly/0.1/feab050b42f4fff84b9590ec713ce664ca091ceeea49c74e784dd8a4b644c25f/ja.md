`shorten(b::Bitly,url::AbstractString)`

`url`を`bit.ly/xXxXx`の短縮リンクに短縮します。

`link`と`response`アイテムを持つ`NamedTuple`を返します。`link`は`bit.ly`リンクで、`response`はBitly APIからの完全な`JSON`レスポンスです。

```julia
b = BitlyToken()
S = shorten(b,"https://docs.julialang.org/en/v1/")
S.link
S.response 
```

`shorten(b::Bitly,url::AbstractString)`

Shorten `url` to a `bit.ly/xXxXx` shortened link.

Returns a `NamedTuple` with `link` and `response` items. `link` is the `bit.ly` link,  while `response` is the complete `JSON` response from the Bitly API.

```julia
b = BitlyToken()
S = shorten(b,"https://docs.julialang.org/en/v1/")
S.link
S.response 
```

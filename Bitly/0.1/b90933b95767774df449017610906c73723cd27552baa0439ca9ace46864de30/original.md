`expand(b::BitlyToken,link::AbstractString)`

Recovers the original `url` from a `bit.ly/xXxXx` shortened link.

Returns a `NamedTuple` with `long_url` and `response` items. `long_url` is the original link,  while `response` is the complete `JSON` response from the Bitly API.

```julia
b = BitlyToken()
S = expand(b,"http://bit.ly/2Us5Vl7")
S.long_url
S.response
```

```
binary(content::Vector{UInt8}; status::Int, headers::Vector{Pair}) :: HTTP.Response
```

バイナリデータとして解釈されるべきUInt8のベクターを返す便利な関数です。

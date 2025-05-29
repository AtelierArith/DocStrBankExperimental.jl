```
json(content::Vector{UInt8}; status::Int, headers::Vector{Pair}) :: HTTP.Response
```

バイナリデータを渡すことができるヘルパー関数で、これはJSONとして解釈されるべきです。コンテンツはすでにバイナリ形式であるため、変換は行われません。

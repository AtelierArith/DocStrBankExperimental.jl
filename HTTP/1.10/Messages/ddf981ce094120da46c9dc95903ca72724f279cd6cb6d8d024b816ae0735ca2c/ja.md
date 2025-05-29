```
HTTP.Response(status, headers::HTTP.Headers, body; request=nothing)
HTTP.Response(status, body)
HTTP.Response(body)
```

HTTPレスポンスメッセージを表し、以下のフィールドを持ちます：

  * `version::HTTPVersion`  [RFC7230 2.6](https://tools.ietf.org/html/rfc7230#section-2.6)
  * `status::Int16`  [RFC7230 3.1.2](https://tools.ietf.org/html/rfc7230#section-3.1.2)  [RFC7231 6](https://tools.ietf.org/html/rfc7231#section-6)
  * `headers::Vector{Pair{String,String}}`  [RFC7230 3.2](https://tools.ietf.org/html/rfc7230#section-3.2)
  * `body::Vector{UInt8}` または `body::IO`  [RFC7230 3.3](https://tools.ietf.org/html/rfc7230#section-3.3)
  * `request`、この `Response` を生成した `Request`。

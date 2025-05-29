```
HTTP.Request(
    method, target, headers=[], body=nobody;
    version=v"1.1", url::URI=URI(), responsebody=nothing, parent=nothing, context=HTTP.Context()
)
```

HTTPリクエストメッセージを表し、以下のフィールドを持ちます：

  * `method::String`  [RFC7230 3.1.1](https://tools.ietf.org/html/rfc7230#section-3.1.1)
  * `target::String`  [RFC7230 5.3](https://tools.ietf.org/html/rfc7230#section-5.3)
  * `version::HTTPVersion`  [RFC7230 2.6](https://tools.ietf.org/html/rfc7230#section-2.6)
  * `headers::HTTP.Headers`  [RFC7230 3.2](https://tools.ietf.org/html/rfc7230#section-3.2)
  * `body::Union{Vector{UInt8}, IO}`  [RFC7230 3.3](https://tools.ietf.org/html/rfc7230#section-3.3)
  * `response`、この`Request`に対する`Response`
  * `url::URI`、リクエストの完全なURI
  * `parent`、このリクエストに至った`Response`（あれば）（例：リダイレクトの場合）。  [RFC7230 6.4](https://tools.ietf.org/html/rfc7231#section-6.4)
  * `context`、ミドルウェアが状態を共有するために使用する`Dict{Symbol, Any}`ストア

```
HTTP.Request(
    method, target, headers=[], body=nobody;
    version=v"1.1", url::URI=URI(), responsebody=nothing, parent=nothing, context=HTTP.Context()
)
```

Represents a HTTP Request Message with fields:

  * `method::String`  [RFC7230 3.1.1](https://tools.ietf.org/html/rfc7230#section-3.1.1)
  * `target::String`  [RFC7230 5.3](https://tools.ietf.org/html/rfc7230#section-5.3)
  * `version::HTTPVersion`  [RFC7230 2.6](https://tools.ietf.org/html/rfc7230#section-2.6)
  * `headers::HTTP.Headers`  [RFC7230 3.2](https://tools.ietf.org/html/rfc7230#section-3.2)
  * `body::Union{Vector{UInt8}, IO}`  [RFC7230 3.3](https://tools.ietf.org/html/rfc7230#section-3.3)
  * `response`, the `Response` to this `Request`
  * `url::URI`, the full URI of the request
  * `parent`, the `Response` (if any) that led to this request (e.g. in the case of a redirect).  [RFC7230 6.4](https://tools.ietf.org/html/rfc7231#section-6.4)
  * `context`, a `Dict{Symbol, Any}` store used by middleware to share state

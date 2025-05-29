A `Response` represents an HTTP response sent to a client by a server. It has six fields:

  * `status`: HTTP status code (see `STATUS_CODES`) [default: `200`]
  * `headers`: `Headers` [default: `HttpCommmon.headers()`]
  * `cookies`: Dictionary of strings => `Cookie`s
  * `data`: the request data as a vector of bytes [default: `UInt8[]`]
  * `finished`: `true` if the `Reponse` is valid, meaning that it can be converted to an actual HTTP response [default: `false`]
  * `requests`: the history of requests that generated the response. Can be greater than one if a redirect was involved.

Response has many constructors - use `methods(Response)` for full list.

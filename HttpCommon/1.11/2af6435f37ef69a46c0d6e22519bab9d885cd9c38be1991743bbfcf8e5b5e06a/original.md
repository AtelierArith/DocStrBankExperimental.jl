A `Request` represents an HTTP request sent by a client to a server. It has five fields:

  * `method`: an HTTP methods string (e.g. "GET")
  * `resource`: the resource requested (e.g. "/hello/world")
  * `headers`: see `Headers` above
  * `data`: the request data as a vector of bytes
  * `uri`: additional details, normally not used

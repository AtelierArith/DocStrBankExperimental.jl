```
set_server(ctx, uri, reset_api_versions=false; max_tries=5, kwargs...)
```

Set the Kubernetes API server endpoint for a context.

Args:

  * ctx: the context for which to set the API server endpoint
  * uri: the API server endpoint uri
  * reset*api*versions: whether to probe the server again for API versions supported (false by default)

Keyword Args:

  * max_tries: retries allowed while probing API versions from server
  * verbose: Log API versions
  * kwargs: other keyword args to pass on while constructing the client for API server (see OpenAPI.jl - https://github.com/JuliaComputing/OpenAPI.jl#readme)

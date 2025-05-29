```
Context(ptr_uri_or_nothing = nothing)
```

Initializes a new Context using the local or the network backend of the IIO library.

This function will create a network context if the IIOD_REMOTE environment variable is set to the hostname where the IIOD server runs. If set to an empty string, the server will be discovered using ZeroConf. If the environment variable is not set, a local context will be created instead.

# Parameters

  * `ptr_uri_or_nothing` : Either a `Ptr{iio_context}`, an URI string (recommended) or `nothing`                        to construct the default context (Linux only).

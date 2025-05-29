```
mutable struct ClientTLSContext
    ptr::Ptr{aws_tls_ctx}
end
```

Client TLS context. A context is expensive, but can be used for the lifetime of the application by all outgoing connections that wish to use the same TLS configuration.

Note on advanced use: the internal constructor on this struct has been left at its default so that you can bring your own native data if you need to. However, you are then responsible for the memory management of that data.

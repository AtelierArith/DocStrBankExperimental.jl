```
mutable struct TLSConnectionOptions
    ptr::Ref{aws_tls_connection_options}
end
```

Connection-specific TLS options. Note that while a TLS context is an expensive object, this object is cheap.

Note on advanced use: the internal constructor on this struct has been left at its default so that you can bring your own native data if you need to. However, you are then responsible for the memory management of that data.

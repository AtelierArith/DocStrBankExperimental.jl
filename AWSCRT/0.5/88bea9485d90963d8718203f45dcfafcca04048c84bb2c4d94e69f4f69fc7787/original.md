```
ClientTLSContext(options::TLSContextOptions)
```

Client TLS context. A context is expensive, but can be used for the lifetime of the application by all outgoing connections that wish to use the same TLS configuration.

Arguments:

  * `options (TLSContextOptions)`: Configuration options.

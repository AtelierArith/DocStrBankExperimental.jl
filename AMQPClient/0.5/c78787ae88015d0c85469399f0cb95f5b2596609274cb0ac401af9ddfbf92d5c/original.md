```
amqps_configure(;
    cacerts = nothing,
    verify = MbedTLS.MBEDTLS_SSL_VERIFY_NONE,
    client_cert = nothing,
    client_key = nothing
)
```

Creates and returns a configuration for making AMQPS connections.

  * cacerts: A CA certificate file (or it's contents) to use for certificate verification.
  * verify: Whether to verify server certificate. Default is false if cacerts is not provided and true if it is.
  * client*cert and client*key: The client certificate and corresponding private key to use. Default is nothing (no client certificate). Values can either be the file name or certificate/key contents.

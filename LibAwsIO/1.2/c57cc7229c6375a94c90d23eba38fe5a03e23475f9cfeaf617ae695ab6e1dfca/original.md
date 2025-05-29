```
aws_tls_ctx_options_init_client_mtls_with_pkcs11(options, allocator, pkcs11_options)
```

Initializes options for use with mutual TLS in client mode, where a PKCS#11 library provides access to the private key.

NOTE: This only works on Unix devices.

# Arguments

  * `options`: [`aws_tls_ctx_options`](@ref) to be initialized.
  * `allocator`: Allocator to use.
  * `pkcs11_options`: Options for using PKCS#11 (contents are copied)

### Prototype

```c
int aws_tls_ctx_options_init_client_mtls_with_pkcs11( struct aws_tls_ctx_options *options, struct aws_allocator *allocator, const struct aws_tls_ctx_pkcs11_options *pkcs11_options);
```

```
aws_tls_ctx_options_set_secitem_options(tls_ctx_options, secitem_options)
```

Applies provided SecItem options to certificate and private key being added to the iOS/tvOS KeyChain.

NOTE: Currently only supported on iOS and tvOS using SecItem.

# Arguments

  * `options`: [`aws_tls_ctx_options`](@ref) to be modified.
  * `secitem_options`: Options for SecItems

### Prototype

```c
int aws_tls_ctx_options_set_secitem_options( struct aws_tls_ctx_options *tls_ctx_options, const struct aws_secitem_options *secitem_options);
```

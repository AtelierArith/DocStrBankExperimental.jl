```
aws_tls_ctx_options_set_keychain_path(options, keychain_path_cursor)
```

!!! compat "Deprecated"



Sets a custom keychain path for storing the cert and pkey with mutual tls in client mode.

NOTE: This only works on MacOS.

### Prototype

```c
int aws_tls_ctx_options_set_keychain_path( struct aws_tls_ctx_options *options, struct aws_byte_cursor *keychain_path_cursor);
```

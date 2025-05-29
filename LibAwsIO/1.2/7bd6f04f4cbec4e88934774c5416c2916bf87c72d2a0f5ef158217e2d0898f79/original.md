```
aws_tls_ctx_options_set_alpn_list(options, alpn_list)
```

Sets alpn list in the form <protocol1;protocol2;...>. A maximum of 4 protocols are supported. alpn_list is copied.

### Prototype

```c
int aws_tls_ctx_options_set_alpn_list(struct aws_tls_ctx_options *options, const char *alpn_list);
```

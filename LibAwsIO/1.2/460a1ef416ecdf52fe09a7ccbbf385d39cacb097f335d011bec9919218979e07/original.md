```
aws_client_bootstrap_set_alpn_callback(bootstrap, on_protocol_negotiated)
```

When using TLS, if ALPN is used, this callback will be invoked from the channel. The returned handler will be added to the channel.

### Prototype

```c
int aws_client_bootstrap_set_alpn_callback( struct aws_client_bootstrap *bootstrap, aws_channel_on_protocol_negotiated_fn *on_protocol_negotiated);
```

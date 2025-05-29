```
aws_tls_client_handler_start_negotiation(handler)
```

Kicks off the negotiation process. This function must be called when in client mode to initiate the TLS handshake. Once the handshake has completed the [`aws_tls_on_negotiation_result_fn`](@ref) will be invoked.

### Prototype

```c
int aws_tls_client_handler_start_negotiation(struct aws_channel_handler *handler);
```

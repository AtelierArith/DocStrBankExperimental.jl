```
aws_server_bootstrap_set_alpn_callback(bootstrap, on_protocol_negotiated)
```

TLSを使用する場合、ALPNが使用されていると、このコールバックはチャネルから呼び出されます。返されたハンドラーはチャネルに追加されます。

### プロトタイプ

```c
int aws_server_bootstrap_set_alpn_callback( struct aws_server_bootstrap *bootstrap, aws_channel_on_protocol_negotiated_fn *on_protocol_negotiated);
```

```
aws_tls_handler_protocol(handler)
```

交渉されたプロトコルのコピーによるバイトバッファを返します。合意されたプロトコルがない場合、lenは0になり、バッファはNULLになります。

### プロトタイプ

```c
struct aws_byte_buf aws_tls_handler_protocol(struct aws_channel_handler *handler);
```

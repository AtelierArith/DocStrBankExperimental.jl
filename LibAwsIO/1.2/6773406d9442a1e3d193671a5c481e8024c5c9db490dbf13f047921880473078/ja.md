```
aws_tls_connection_options_copy(to, from)
```

'to'をクリーンアップし、'from'を'to'にコピーします。'to'は初期化されている必要があります。

### プロトタイプ

```c
int aws_tls_connection_options_copy( struct aws_tls_connection_options *to, const struct aws_tls_connection_options *from);
```

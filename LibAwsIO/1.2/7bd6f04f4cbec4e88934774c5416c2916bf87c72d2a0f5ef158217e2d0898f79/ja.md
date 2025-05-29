```
aws_tls_ctx_options_set_alpn_list(options, alpn_list)
```

<protocol1;protocol2;...>の形式でalpnリストを設定します。最大4つのプロトコルがサポートされています。alpn_listはコピーされます。

### プロトタイプ

```c
int aws_tls_ctx_options_set_alpn_list(struct aws_tls_ctx_options *options, const char *alpn_list);
```

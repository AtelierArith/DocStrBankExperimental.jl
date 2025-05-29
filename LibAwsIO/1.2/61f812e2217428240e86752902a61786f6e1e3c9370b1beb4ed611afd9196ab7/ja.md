```
aws_tls_connection_options_clean_up(connection_options)
```

[`aws_tls_connection_options`](@ref) のリソースをクリーンアップします。これは、tls ハンドラーを初期化した直後、またはブートストラップ API を使用している場合は、チャネルを要求した直後に呼び出すことができます。

### プロトタイプ

```c
void aws_tls_connection_options_clean_up(struct aws_tls_connection_options *connection_options);
```

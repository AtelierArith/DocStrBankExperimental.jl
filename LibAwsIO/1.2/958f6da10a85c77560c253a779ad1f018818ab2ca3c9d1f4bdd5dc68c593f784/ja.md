```
aws_tls_ctx_options_override_default_trust_store_from_path(options, ca_path, ca_file)
```

デフォルトの信頼ストアを上書きします。ca*pathは、信頼された証明書を含むディスク上のディレクトリへのパスです。これはUnixシステムでのみサポートされています（それ以外の場合、このパラメータは無視されます）。ca*fileは、信頼された証明書を含むディスク上のファイルへのパスです。ca_fileはディスクから読み込まれ、内部バッファに格納されます。

### プロトタイプ

```c
int aws_tls_ctx_options_override_default_trust_store_from_path( struct aws_tls_ctx_options *options, const char *ca_path, const char *ca_file);
```

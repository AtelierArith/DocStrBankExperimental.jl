```
aws_tls_ctx_options_override_default_trust_store(options, ca_file)
```

デフォルトの信頼ストアを上書きします。ca*fileは、信頼されたCA証明書のPEM形式のチェーンを含むバッファです。ca*fileはコピーされます。

### プロトタイプ

```c
int aws_tls_ctx_options_override_default_trust_store( struct aws_tls_ctx_options *options, const struct aws_byte_cursor *ca_file);
```

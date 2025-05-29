```
aws_s3_init_default_signing_config(signing_config, region, credentials_provider)
```

デフォルトのS3署名の設定を初期化します。

### プロトタイプ

```c
void aws_s3_init_default_signing_config( struct aws_signing_config_aws *signing_config, const struct aws_byte_cursor region, struct aws_credentials_provider *credentials_provider);
```

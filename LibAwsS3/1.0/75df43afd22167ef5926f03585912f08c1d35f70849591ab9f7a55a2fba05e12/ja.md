```
aws_s3express_credentials_provider_get_credentials(provider, original_credentials, properties, callback, user_data)
```

プロパティに基づいて特定の資格情報を取得するための非同期関数です。

callbackは、戻り値がAWS*OP*SUCCESSであった場合にのみ呼び出されます。

# 引数

  * `provider`: [`aws_s3express_credentials_provider`](@ref) から取得するプロバイダー
  * `original_credentials`: S3 Expressの資格情報を導出するために使用される資格情報。
  * `properties`: 取得される資格情報の特定のプロパティ。
  * `user_data`: 完了コールバックに渡すユーザーデータ

### プロトタイプ

```c
int aws_s3express_credentials_provider_get_credentials( struct aws_s3express_credentials_provider *provider, const struct aws_credentials *original_credentials, const struct aws_credentials_properties_s3express *properties, aws_on_get_credentials_callback_fn callback, void *user_data);
```

```
aws_s3express_credentials_provider_init_base(provider, allocator, vtable, impl)
```

プロバイダーを基本的な vtable と参照カウントで初期化します。そして、参照カウントを vtable 関数に接続します。

# 引数

  * `provider`:
  * `allocator`:
  * `vtable`:
  * `impl`: オプション、プロバイダーのための impl

# 戻り値

[`AWS_S3_API`](@ref)

### プロトタイプ

```c
void aws_s3express_credentials_provider_init_base( struct aws_s3express_credentials_provider *provider, struct aws_allocator *allocator, struct aws_s3express_credentials_provider_vtable *vtable, void *impl);
```

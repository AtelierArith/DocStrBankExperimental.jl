```
aws_pkcs11_lib_new(allocator, options)
```

PKCS#11ライブラリをロードして初期化します。オプションについては[`aws_pkcs11_lib_options`](@ref)を参照してください。

成功した場合、有効なポインタが返されます。使用が終わったら[`aws_pkcs11_lib_release`](@ref)()を呼び出す必要があります。失敗した場合はNULLが返され、エラーが設定されます。

### プロトタイプ

```c
struct aws_pkcs11_lib *aws_pkcs11_lib_new( struct aws_allocator *allocator, const struct aws_pkcs11_lib_options *options);
```

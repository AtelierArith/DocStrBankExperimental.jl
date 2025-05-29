```
aws_pkcs11_lib_acquire(pkcs11_lib)
```

PKCS#11ライブラリへの参照を取得し、それがクリーンアップされるのを防ぎます。使用が終わったら、[`aws_pkcs11_lib_release`](@ref)()を呼び出す必要があります。この関数は、渡されたものをそのまま返します。失敗することはありません。

### プロトタイプ

```c
struct aws_pkcs11_lib *aws_pkcs11_lib_acquire(struct aws_pkcs11_lib *pkcs11_lib);
```

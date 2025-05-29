```
aws_pkcs11_lib_release(pkcs11_lib)
```

PKCS#11ライブラリへの参照を解放します。最後の参照が解放されると、ライブラリはクリーンアップされます。

### プロトタイプ

```c
void aws_pkcs11_lib_release(struct aws_pkcs11_lib *pkcs11_lib);
```

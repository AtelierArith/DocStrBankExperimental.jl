```
aws_tls_is_cipher_pref_supported(cipher_pref)
```

この関数は、基盤となるTLS実装でこの暗号プリファレンスが利用可能であればtrueを返します。この関数は、暗号プリファレンスを設定する前に常に呼び出すべきです。

### プロトタイプ

```c
bool aws_tls_is_cipher_pref_supported(enum aws_tls_cipher_pref cipher_pref);
```

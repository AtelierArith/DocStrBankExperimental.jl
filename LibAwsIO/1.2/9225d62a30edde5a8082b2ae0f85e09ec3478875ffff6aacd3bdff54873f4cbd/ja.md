```
aws_tls_is_alpn_available()
```

基盤となる tls 実装で alpn が利用可能な場合は true を返します。この関数は、alpn リストを設定する前に常に呼び出す必要があります。

### プロトタイプ

```c
bool aws_tls_is_alpn_available(void);
```

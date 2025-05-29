```
aws_tls_signature_algorithm_str(signature)
```

与えられた列挙型に対して、次のような文字列を返します: AWS*TLS*SIGNATURE_RSA -> "RSA"

### プロトタイプ

```c
const char *aws_tls_signature_algorithm_str(enum aws_tls_signature_algorithm signature);
```

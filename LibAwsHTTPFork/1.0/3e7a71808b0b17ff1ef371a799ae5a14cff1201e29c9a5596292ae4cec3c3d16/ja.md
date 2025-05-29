```
aws_http_message_get_headers(message)
```

このデータ構造体には、[`aws_http_message`](@ref) データ構造体で利用可能なヘッダーの検査および変更のための関数がより多く含まれています。

### プロトタイプ

```c
struct aws_http_headers *aws_http_message_get_headers(const struct aws_http_message *message);
```

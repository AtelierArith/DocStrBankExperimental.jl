```
aws_http_status_text(status_code)
```

一般的なステータスコードの説明を返します。例: 404 -> "Not Found" ステータスコードが認識されない場合は空の文字列が返されます。

### プロトタイプ

```c
const char *aws_http_status_text(int status_code);
```

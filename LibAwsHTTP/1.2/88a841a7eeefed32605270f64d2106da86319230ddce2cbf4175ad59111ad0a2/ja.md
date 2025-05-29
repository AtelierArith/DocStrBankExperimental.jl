```
aws_http_headers_acquire(headers)
```

オブジェクトの保持を取得し、[`aws_http_headers_release`](@ref)() が保持しているすべての人によって呼び出されるまで削除されないようにします。

### プロトタイプ

```c
void aws_http_headers_acquire(struct aws_http_headers *headers);
```

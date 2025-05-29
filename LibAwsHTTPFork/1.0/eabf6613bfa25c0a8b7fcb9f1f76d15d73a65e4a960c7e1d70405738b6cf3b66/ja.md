```
aws_http_message_acquire(message)
```

オブジェクトの保持を取得し、[`aws_http_message_release`](@ref)() が保持しているすべての人によって呼び出されるまで削除されないようにします。

この関数は、渡されたメッセージ（NULLの可能性あり）を返し、単一のステートメントで取得と代入を行えるようにします。

### プロトタイプ

```c
struct aws_http_message *aws_http_message_acquire(struct aws_http_message *message);
```

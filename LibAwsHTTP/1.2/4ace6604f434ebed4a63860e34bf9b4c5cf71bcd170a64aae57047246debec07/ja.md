```
aws_http_message_release(message)
```

オブジェクトの保持を解除します。すべての保持が解除されると、オブジェクトは削除されます。

この関数は常にNULLを返すため、release-and-assign-NULLを1つのステートメントで行うことができます。

### プロトタイプ

```c
struct aws_http_message *aws_http_message_release(struct aws_http_message *message);
```

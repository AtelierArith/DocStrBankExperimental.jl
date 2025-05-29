```
aws_async_input_stream_release(stream)
```

参照カウントを減少させます。NULLを渡すことができます（効果はありません）。常にNULLを返します。

### プロトタイプ

```c
struct aws_async_input_stream *aws_async_input_stream_release(struct aws_async_input_stream *stream);
```

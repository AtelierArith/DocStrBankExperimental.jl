```
aws_async_input_stream_acquire(stream)
```

参照カウントを増加させます。NULLを渡すこともできます（効果はありません）。渡されたポインタをそのまま返します。

### プロトタイプ

```c
struct aws_async_input_stream *aws_async_input_stream_acquire(struct aws_async_input_stream *stream);
```

```
aws_input_stream_release(stream)
```

入力ストリームの参照カウントを減少させます。参照カウントがゼロになると、入力ストリームは破棄されます。

常にNULLを返します。

### プロトタイプ

```c
struct aws_input_stream *aws_input_stream_release(struct aws_input_stream *stream);
```

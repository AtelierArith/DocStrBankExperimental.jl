```
aws_input_stream_acquire(stream)
```

入力ストリームの参照カウントを増加させ、呼び出し元がそれを参照できるようにします。

渡されたのと同じ入力ストリームを返します。

### プロトタイプ

```c
struct aws_input_stream *aws_input_stream_acquire(struct aws_input_stream *stream);
```

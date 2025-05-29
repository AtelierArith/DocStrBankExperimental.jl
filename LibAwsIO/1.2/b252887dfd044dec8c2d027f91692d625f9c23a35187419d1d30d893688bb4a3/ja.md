```
testing_channel_push_read_data(channel, data)
```

[`aws_io_message`](@ref)を作成し、次のデータを含め、読み取り方向でチャネルにプッシュします。

### プロトタイプ

```c
static inline int testing_channel_push_read_data(struct testing_channel *channel, struct aws_byte_cursor data);
```

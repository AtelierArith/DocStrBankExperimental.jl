```
testing_channel_push_write_data(channel, data)
```

[`aws_io_message`](@ref)を作成し、次のデータを含め、書き込み方向にチャンネルにプッシュします。

### プロトタイプ

```c
static inline int testing_channel_push_write_data(struct testing_channel *channel, struct aws_byte_cursor data);
```

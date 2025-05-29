```
testing_channel_push_write_str(channel, str)
```

[`aws_io_message`](@ref)を作成し、以下のデータを含め、書き込み方向にチャンネルにプッシュします。

### プロトタイプ

```c
static inline int testing_channel_push_write_str(struct testing_channel *channel, const char *str);
```

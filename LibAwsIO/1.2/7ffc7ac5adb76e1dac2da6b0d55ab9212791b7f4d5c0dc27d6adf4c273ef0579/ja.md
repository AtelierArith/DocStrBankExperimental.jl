```
testing_channel_push_read_str(channel, str)
```

[`aws_io_message`](@ref)を作成し、以下のデータを含め、チャネルを読み取り方向にプッシュします。

### プロトタイプ

```c
static inline int testing_channel_push_read_str(struct testing_channel *channel, const char *str);
```

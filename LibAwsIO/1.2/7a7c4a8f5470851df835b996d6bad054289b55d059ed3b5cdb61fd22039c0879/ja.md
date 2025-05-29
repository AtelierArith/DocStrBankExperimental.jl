```
testing_channel_push_read_str_ignore_errors(channel, str)
```

[`aws_io_message`](@ref)を作成し、以下のデータを含めます。メッセージを読み取り方向にチャンネルにプッシュしようとしますが、メッセージを送信できない場合はアサートしません。ハンドラのシャットダウン中に到着するデータをテストするのに便利です。

### プロトタイプ

```c
static inline int testing_channel_push_read_str_ignore_errors(struct testing_channel *channel, const char *str);
```

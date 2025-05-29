```
aws_channel_destroy(channel)
```

チャネルを、すべてのスロットとハンドラと共に、破棄のためにマークします。シャットダウンが完了した後に呼び出す必要があります。`[`aws*channel*shutdown`](@ref)()` が完了している場合、任意のスレッドから呼び出すことができます。チャネルに対して [`aws_channel_acquire_hold`](@ref)() を介して保持を取得したすべてのユーザーが、それを [`aws_channel_release_hold`](@ref)() を介して解放するまで、メモリは解放されないことに注意してください。

### プロトタイプ

```c
void aws_channel_destroy(struct aws_channel *channel);
```

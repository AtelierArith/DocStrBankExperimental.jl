```
aws_channel_shutdown(channel, error_code)
```

チャネルのシャットダウンを開始します。シャットダウンは最も左のスロットから始まります。各ハンドラーは、読み取り方向のシャットダウンプロセスが完了したら、'[`aws_channel_slot_on_handler_shutdown_complete`](@ref)'を呼び出します。最も右のスロットが読み取り方向でシャットダウンすると、プロセスは最も右のスロットからシャットダウンを開始します。最も左のスロットが書き込み方向でシャットダウンすると、'callbacks->shutdown_completed'がイベントループのスレッドで呼び出されます。

この関数は任意のスレッドから呼び出すことができます。

### プロトタイプ

```c
int aws_channel_shutdown(struct aws_channel *channel, int error_code);
```

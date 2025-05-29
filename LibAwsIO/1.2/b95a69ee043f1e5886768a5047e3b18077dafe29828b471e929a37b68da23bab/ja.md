```
aws_channel_set_statistics_handler(channel, handler)
```

チャネルに統計ハンドラーを設定します。統計ハンドラーで計測されている間、チャネルは定期的にハンドラーのパフォーマンスと状態に関するチャネルごとの特定の統計を報告します。

チャネルに統計ハンドラーを割り当てることは所有権の移転です – チャネルはハンドラーを適切にクリーンアップします。統計ハンドラーは動的に変更することができます（例えば、バニラのhttpチャネルからwebsocketチャネルへのアップグレードなど）が、この関数はチャネルが属するイベントループスレッドからのみ呼び出すことができます。

統計ハンドラーを設定するための最初のフックは、チャネルの作成コールバックです。

### プロトタイプ

```c
int aws_channel_set_statistics_handler(struct aws_channel *channel, struct aws_crt_statistics_handler *handler);
```

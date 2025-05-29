```
aws_channel_trigger_read(channel)
```

外部プロセスがデータソースチャネルハンドラによる読み取りを強制する方法。サーバーチャネルが初期ハンドラの設定を完了したときなど、特定のケースで必要です。この場合、ソケット上で読み取りがすでにトリガーされている可能性があり（例えば、クライアントのCLIENT_HELLO tlsペイロード）、さらなるデータ/通知がない場合、このデータは決して処理されません。

### プロトタイプ

```c
int aws_channel_trigger_read(struct aws_channel *channel);
```

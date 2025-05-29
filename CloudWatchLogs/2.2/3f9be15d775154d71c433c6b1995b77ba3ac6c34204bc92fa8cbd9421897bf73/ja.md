```
CloudWatchLogHandler(
    config::AWSConfig,
    log_group_name,
    log_stream_name,
    formatter::Memento.Formatter,
)
```

CloudWatch Log Streamにログを記録するためのMementoハンドラーを構築します。このコンストラクタは、ストリームにログを非同期的に送信するタスクを作成します。

CloudWatch Log Eventには、`timestamp`と`message`の2つのプロパティのみがあります。

`Record`に`date`プロパティがある場合、それが`timestamp`として使用されます。そうでない場合、`Memento.emit`が呼び出されたときに現在の時刻がキャプチャされます。すべての`DateTime`はUTCであると仮定されます。

`message`は、このハンドラーの`formatter`を使用して`Record`に対して`Memento.format`を呼び出すことによって生成されます。

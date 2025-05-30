```
notify_register(protocol::MQTTProtocol, aid::String; kwargs...)
```

`aid`を持つ新しいエージェントが登録されたことを`protocol` MQTTクライアントに通知します。

登録には、エージェントがサブスクライブするためのkwarg `topics`が必要です。クライアントがまだサブスクライブしていないトピックがあれば、それに対して`subscribe`が呼び出されます。

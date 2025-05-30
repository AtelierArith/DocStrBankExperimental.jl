```
notify_register(protocol::MQTTProtocol, aid::String; kwargs...)
```

`aid`を持つ新しいエージェントが登録されたことを`protocol` MQTTクライアントに通知します。

登録には、エージェントが購読するためのkwarg `topics`が必要です。クライアントがまだ購読していないトピックがある場合は、それに対して`subscribe`が呼び出されます。

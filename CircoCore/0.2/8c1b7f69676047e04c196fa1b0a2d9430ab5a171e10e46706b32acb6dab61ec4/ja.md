```
fire(service, me::Actor, event::Event)
```

アクターでイベントを発火し、アクターのイベントディスパッチャーによって配信されます。

イベントを発火するには、アクターに `eventdispatcher::Addr` フィールドが必要であり、これは自動的に設定されます。

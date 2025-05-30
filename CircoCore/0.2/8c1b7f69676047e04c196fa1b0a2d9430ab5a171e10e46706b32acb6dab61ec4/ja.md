```
fire(service, me::Actor, event::Event)
```

アクターでイベントを発火させ、アクターのイベントディスパッチャーによって配信されます。

イベントを発火させるには、アクターに `eventdispatcher::Addr` フィールドが必要であり、これは自動的に設定されます。

```
min_enabled_level!(logger::MutableLogLevelLogger, level) -> LogLevel
```

`logger`の最小有効レベルを`level`に設定します。例えば、すべてのメッセージがフィルタリングされるレベル以下または等しい低いレベルです。

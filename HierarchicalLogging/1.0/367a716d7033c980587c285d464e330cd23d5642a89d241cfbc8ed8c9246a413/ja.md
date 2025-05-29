```
insert_logger!(loggers::HierarchicalLogger, key, logger, [level=min_enabled_level(logger)])
```

`logger`を関連付けられた`key`と共に`loggers`に追加します。存在しない場合に限ります。

`key`を持つ既存のロガーが`loggers`に存在する場合、`ArgumentException`をスローします。

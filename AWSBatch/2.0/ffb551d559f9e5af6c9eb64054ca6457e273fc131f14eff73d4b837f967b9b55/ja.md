```
log_events(log_group, log_stream) -> Union{Vector{LogEvent}, Nothing}
```

指定されたロググループとストリームからCloudWatchログを`LogEvent`の`Vector`として取得します。ログストリームが存在しない場合は`nothing`が返されます。

```julia
LogEventTracker() -> InfrastructureSystems.LogEventTracker
LogEventTracker(
    levels
) -> InfrastructureSystems.LogEventTracker

```

すべてのログイベントのカウントをレベル別に追跡します。

# 例

```Julia
LogEventTracker()
LogEventTracker((Logging.Info, Logging.Warn, Logging.Error))
```

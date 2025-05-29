```
notice(logger::Logger, msg::AbstractString)
```

通知レベルでメッセージをログに記録します。

```
notice(msg::Function, logger::Logger)
```

提供された関数によって生成されたメッセージを通知レベルでログに記録します。

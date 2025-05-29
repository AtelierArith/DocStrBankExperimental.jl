```
warn(logger::Logger, exc::Exception)
warn(logger::Logger, msg, exc::Exception)
```

例外を受け取り、それをログに記録します。例外が `CompositeException` の場合、含まれる各例外がログに記録されます。

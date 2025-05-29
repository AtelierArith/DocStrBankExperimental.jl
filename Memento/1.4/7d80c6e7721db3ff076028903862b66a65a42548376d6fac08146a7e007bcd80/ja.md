```
error(logger::Logger, msg::AbstractString)
```

エラーレベルでメッセージをログに記録し、そのメッセージで `ErrorException` をスローします。

```
error(msg::Function, logger::Logger)
```

提供された関数によって生成されたメッセージをエラーレベルでログに記録し、そのメッセージで `ErrorException` をスローします。

```
error(logger::Logger, exc::Exception)
```

`Exception` の内容で `error(logger, msg)` を呼び出し、その後 `Exception` をスローします。例外が `CompositeException` の場合、含まれる各例外がログに記録され、その後 `CompositeException` がスローされます。

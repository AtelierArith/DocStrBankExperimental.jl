```
emergency(logger::Logger, msg::AbstractString)
```

緊急レベルでメッセージをログに記録し、そのメッセージで `ErrorException` をスローします。

```
emergency(msg::Function, logger::Logger)
```

提供された関数によって生成されたメッセージを緊急レベルでログに記録し、そのメッセージで `ErrorException` をスローします。

```
emergency(logger::Logger, exc::Exception)
```

`Exception` の内容で `emergency(logger, msg)` を呼び出し、その後 `Exception` をスローします。例外が `CompositeException` の場合、含まれる各例外がログに記録され、その後 `CompositeException` がスローされます。

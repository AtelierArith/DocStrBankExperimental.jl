```
critical(logger::Logger, msg::AbstractString)
```

クリティカルレベルでメッセージをログに記録し、そのメッセージで`ErrorException`をスローします。

```
critical(msg::Function, logger::Logger)
```

提供された関数によって生成されたメッセージをクリティカルレベルでログに記録し、そのメッセージで`ErrorException`をスローします。

```
critical(logger::Logger, exc::Exception)
```

`Exception`の内容で`critical(logger, msg)`を呼び出し、その後`Exception`をスローします。例外が`CompositeException`の場合、含まれる各例外がログに記録され、その後`CompositeException`がスローされます。

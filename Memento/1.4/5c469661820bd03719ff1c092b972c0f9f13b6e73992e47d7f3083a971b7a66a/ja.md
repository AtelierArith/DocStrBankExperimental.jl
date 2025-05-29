```
alert(logger::Logger, msg::AbstractString)
```

アラートレベルでメッセージをログに記録し、そのメッセージで`ErrorException`をスローします。

```
alert(msg::Function, logger::Logger)
```

提供された関数によって生成されたメッセージをアラートレベルでログに記録し、そのメッセージで`ErrorException`をスローします。

```
alert(logger::Logger, exc::Exception)
```

`Exception`の内容で`alert(logger, msg)`を呼び出し、その後`Exception`をスローします。例外が`CompositeException`の場合、含まれる各例外がログに記録され、その後`CompositeException`がスローされます。

```
alert(logger::Logger, msg::AbstractString)
```

Logs the message at the alert level and throws an `ErrorException` with that message

```
alert(msg::Function, logger::Logger)
```

Logs the message produced by the provided function at the alert level and throws an `ErrorException` with that message.

```
alert(logger::Logger, exc::Exception)
```

Calls `alert(logger, msg)` with the contents of the `Exception`, then throw the `Exception`. If the exception is a `CompositeException`, each contained exception is logged, then the `CompositeException` is thrown.

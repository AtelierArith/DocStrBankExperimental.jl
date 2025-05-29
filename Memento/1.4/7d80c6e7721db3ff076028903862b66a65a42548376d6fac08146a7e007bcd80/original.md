```
error(logger::Logger, msg::AbstractString)
```

Logs the message at the error level and throws an `ErrorException` with that message

```
error(msg::Function, logger::Logger)
```

Logs the message produced by the provided function at the error level and throws an `ErrorException` with that message.

```
error(logger::Logger, exc::Exception)
```

Calls `error(logger, msg)` with the contents of the `Exception`, then throw the `Exception`. If the exception is a `CompositeException`, each contained exception is logged, then the `CompositeException` is thrown.

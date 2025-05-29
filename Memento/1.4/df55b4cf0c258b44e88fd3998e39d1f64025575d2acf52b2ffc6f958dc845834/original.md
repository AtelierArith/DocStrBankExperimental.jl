```
critical(logger::Logger, msg::AbstractString)
```

Logs the message at the critical level and throws an `ErrorException` with that message

```
critical(msg::Function, logger::Logger)
```

Logs the message produced by the provided function at the critical level and throws an `ErrorException` with that message.

```
critical(logger::Logger, exc::Exception)
```

Calls `critical(logger, msg)` with the contents of the `Exception`, then throw the `Exception`. If the exception is a `CompositeException`, each contained exception is logged, then the `CompositeException` is thrown.

```
emergency(logger::Logger, msg::AbstractString)
```

Logs the message at the emergency level and throws an `ErrorException` with that message

```
emergency(msg::Function, logger::Logger)
```

Logs the message produced by the provided function at the emergency level and throws an `ErrorException` with that message.

```
emergency(logger::Logger, exc::Exception)
```

Calls `emergency(logger, msg)` with the contents of the `Exception`, then throw the `Exception`. If the exception is a `CompositeException`, each contained exception is logged, then the `CompositeException` is thrown.

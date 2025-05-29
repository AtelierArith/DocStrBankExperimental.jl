```
warn(logger::Logger, exc::Exception)
warn(logger::Logger, msg, exc::Exception)
```

Takes an exception and logs it. If the exception is a `CompositeException`, each contained exception is logged.

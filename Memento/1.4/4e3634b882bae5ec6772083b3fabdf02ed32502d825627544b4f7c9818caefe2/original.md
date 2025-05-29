```
Record
```

A dictionary-like container with `Symbol` keys used to store information about a log events including the msg, date, level, stacktrace, etc. `Formatter`s use `Records` to format log message strings.

You can access the properties of a `Record` by using `getproperty` (ie: record.msg).

Subtypes of `Record` should implement `getproperty(::MyRecord, ::Symbol)` and key-value pair iteration.

```
Handler
```

Manage formatting `Record`s and logging the resulting `String`. All `Handler` subtypes must implement at least 1 `log(::Handler, ::Record)` method.

NOTE: Handlers can be useful if you need to special case logging behaviour based on the `Formatter`, `IO` and/or `Record` types.

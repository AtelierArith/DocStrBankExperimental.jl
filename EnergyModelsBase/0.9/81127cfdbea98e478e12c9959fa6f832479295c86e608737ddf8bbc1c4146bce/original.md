```
assert_or_log(ex, msg)
```

Macro that extends the behaviour of the `@assert` macro. The switch `ASSERTS_AS_LOG`, controls if the macro should act as a logger or a normal `@assert`. This macro is designed to be used to check whether the data provided is consistent.

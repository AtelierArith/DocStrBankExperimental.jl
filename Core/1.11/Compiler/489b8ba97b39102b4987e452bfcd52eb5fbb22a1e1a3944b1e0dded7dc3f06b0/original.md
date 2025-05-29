```
info::MethodResultPure <: CallInfo
```

This struct represents a method result constant was proven to be effect-free, including being no-throw (typically because the value was computed by calling an `@pure` function).

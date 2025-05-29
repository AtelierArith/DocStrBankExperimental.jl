```
already_inferred_quick_test(::AbstractInterpreter, ::MethodInstance)
```

For the `NativeInterpreter`, we don't need to do an actual cache query to know if something was already inferred. If we reach this point, but the inference flag has been turned off, then it's in the cache. This is purely for a performance optimization.

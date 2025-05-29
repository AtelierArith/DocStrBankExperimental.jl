```
MultipleExceptions(exception1, exception2, ...)
MultipleExceptions(tuple_or_vector_of_exceptions)
```

Little helper type which combines several Exceptions into one new Exception.

In the several arguments version, and only there, if an MultipleExceptions is given, it will be flattened directly for convenience.

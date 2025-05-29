```
unwrap_error(result::Result{T, E}) -> E
unwrap_error(exception::E) -> E
```

Assumes `result` holds an exception of type `E` and returns it. If `result` holds a value instead, throw an exception.

If `unwrap_error`'s argument is an `Exception`, that exception is returned.

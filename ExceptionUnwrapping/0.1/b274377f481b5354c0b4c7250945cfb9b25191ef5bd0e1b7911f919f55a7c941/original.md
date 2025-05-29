```
is_wrapped_exception(e)::Bool
```

Returns true if the given exception instance, `e` is a wrapped exception, such that `unwrap_exception(e)` would return something different than `e`.

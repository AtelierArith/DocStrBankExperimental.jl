```
unwrap(result::Result{T, E}) -> T
unwrap(val::T) -> T
unwrap(::Type{T}, result_or_val) -> T
```

Assumes `result` holds a value of type `T` and returns it. If `result` holds an exception instead, that exception is thrown.

If `unwrap`'s argument is not a `Result`, it is returned.

The two-argument form of `unwrap` calls `unwrap` on its second argument, then converts it to type `T`.

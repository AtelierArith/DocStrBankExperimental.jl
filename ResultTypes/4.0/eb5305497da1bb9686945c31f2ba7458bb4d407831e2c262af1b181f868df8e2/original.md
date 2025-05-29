```
Result(val::T, exception_type::Type{E}=Exception) -> Result{T, E}
```

Create a `Result` that could hold a value of type `T` or an exception of type `E`, and store `val` in it. If the exception type is not provided, the supertype `Exception` is used as `E`.

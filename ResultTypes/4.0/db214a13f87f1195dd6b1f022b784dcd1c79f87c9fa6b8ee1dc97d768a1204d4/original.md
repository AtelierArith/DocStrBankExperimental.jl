```
ErrorResult(::Type{T}, exception::E) -> Result{T, E}
ErrorResult(::Type{T}, exception::AbstractString="") -> Result{T, ErrorException}
```

Create a `Result` that could hold a value of type `T` or an exception of type `E`, and store `exception` in it. If the `exception` is provided as text, it is wrapped in the generic `ErrorException`. If no exception is provided, an `ErrorException` with an empty string is used. If the type argument is not provided, `Any` is used.

`ErrorResult` is a convenience function for creating a `Result` and is not its own type.

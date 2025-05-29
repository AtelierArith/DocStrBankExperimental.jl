```
unwrap_exception(exception_wrapper) -> wrapped_exception
unwrap_exception(normal_exception) -> normal_exception

# Add overrides for custom exception types
ExceptionUnwrapping.unwrap_exception(e::MyWrappedException) = e.wrapped_exception
```

Unwraps a wrapped exception by one level. *New wrapped exception types should add a method to this function.*

One example of a wrapped exception is the `TaskFailedException`, which wraps an exception thrown by a `Task` with a new `Exception` describing the task failure.

It is useful to unwrap the exception to test what kind of exception was thrown in the first place, which is useful in case you need different exception handling behavior for different types of exceptions.

Authors of new wrapped exception types can overload this to indicate what field their exception is wrapping, by adding an overload, e.g.:

```julia
ExceptionUnwrapping.unwrap_exception(e::MyWrappedException) = e.wrapped_exception
```

This is used in the implementations of the other functions in the module:

  * [`has_wrapped_exception(e, ::Type)`](@ref)
  * [`unwrap_exception_to_root(e)`](@ref)

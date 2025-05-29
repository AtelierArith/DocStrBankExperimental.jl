```
has_wrapped_exception(e, ExceptionType)::Bool
```

Returns true if the given exception instance, `e`, contains an exception of type `T` anywhere in its chain of unwrapped exceptions.

Application code should prefer to use `has_wrapped_exception(e, T)` instead of `e isa T` in catch-blocks, to keep code from breaking when libraries wrap user's exceptions.

This makes application code resilient to library changes that may cause wrapped exceptions, such as e.g. changes to underlying concurrency decisions (thus maintaining concurrency's cooperative benefits).

# Example

```julia
try
    # If this becomes concurrent in the future, the catch-block doesn't need to change.
    library_function(args...)
catch e
    if has_wrapped_exception(e, MyExceptionType)
        unwrapped = unwrap_exception_until(e, MyExceptionType)
        handle_my_exception(unwrapped, caught=e)
    else
        rethrow()
    end
end
```

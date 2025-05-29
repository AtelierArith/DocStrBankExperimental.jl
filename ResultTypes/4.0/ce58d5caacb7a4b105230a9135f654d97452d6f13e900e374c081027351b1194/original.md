```
@try x
@try(x)
```

if `x` is an error (i.e., `iserror(x) == true`), unwrap the error and return from the current function.  Otherwise, unwrap `x`.

If the unwrapped exception is of the wrong type, there must be a `Base.convert` method which will convert it to the correct type.  (See the example in the extended help below.)

This macro is meant to reduce boilerplate when calling functions returning `Result`s.

# Extended help

A typical set of functions using `ResultTypes` might look something like this:

```julia
Base.convert(::Type{FooError}, err::BarError) = FooError("Got a BarError: $(err.msg)")

function isbar(y)::Result{Bool, BarError}
    bad_value(y) && return BarError("Bad value: $y")
    return y == "bar"
end

function foo(x)::Result{Int, FooError}
    result = isbar(x)
    ResultTypes.iserror(result) && return unwrap_error(result)
    is_b = unwrap(result)

    return is_b ? 42 : 13
end
```

With the `@try` macro, `foo` gets shortened to

```julia
function foo(x)::Result{Int, FooError}
    is_b = @try(isbar(x))
    return is_b ? 42 : 13
end
```

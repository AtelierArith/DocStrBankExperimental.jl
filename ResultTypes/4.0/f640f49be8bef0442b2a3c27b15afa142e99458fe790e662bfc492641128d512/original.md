```
@try x err
@try(x, err)
```

if `x` is an error, return a new exception `err`.  Otherwise, unwrap `x`.

This version of @try does not require any exceptions to be converted.

# Extended help

Example:

```julia
function isbar(y)::Result{Bool, BarError}
    bad_value(y) && return BarError("Bad value: $y")
    return y == "bar"
end

function foo(x)::Result{Int, FooError}
    is_b = @try(isbar(x), FooError())
    return is_b ? 42 : 13
end
```

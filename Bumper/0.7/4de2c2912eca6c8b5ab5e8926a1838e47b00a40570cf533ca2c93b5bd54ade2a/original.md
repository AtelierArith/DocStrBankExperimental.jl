```
@no_escape([buf=default_buffer()], expr)
```

Record the current state of `buf` (which defaults to the `default_buffer()` if there is only one argument), and then run the code in `expr` and then reset `buf` back to the state it was in before the code ran. This allows us to allocate memory within the `expr` using `@alloc`, and then have those arrays be automatically de-allocated once the expression is over. This is a restrictive but highly efficient form of memory management.

See also `Bumper.checkpoint_save`, and `Bumper.checkpoint_restore!`.

Using `return`, `@goto`, and `@label` are not allowed inside of `@no_escape` block.

Example:

```
function f(x::Vector{Int})
    # Set up a scope where memory may be allocated, and does not escape:
    @no_escape begin
        # Allocate a `UnsafeArray` from UnsafeArrays.jl using memory from the default buffer.
        y = @alloc(Int, length(x))
        # Now do some stuff with that vector:
        y .= x .+ 1
       sum(y)
    end
end
```

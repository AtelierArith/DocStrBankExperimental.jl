```
@ref ~lifetime [:mut] var = value
@ref ~lifetime [:mut] (var1, var2, ...) = (value1, value2, ...)
@ref ~lifetime [:mut] for var in iter
    # body
end
```

Create a reference to an owned value within a lifetime scope. See the `@lifetime` macro for more information on lifetime scopes.

If `:mut` is specified, creates a mutable reference. Otherwise, creates an immutable reference. Returns a Borrowed{T} or BorrowedMut{T} that forwards access to the underlying value.

!!! warning
    This will not detect aliasing in the iterator.


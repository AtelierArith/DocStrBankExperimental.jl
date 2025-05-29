```
@bc func(args...; kwargs...)
```

Calls `func` with the given arguments and keyword arguments, automatically creating temporary borrows for arguments that appear to be owned variables.

# Examples

Say that we wish to safely modify an array by reference. We have two owned variables, `ar1` and `ar2`, and we wish to add the first element of `ar2` to `ar1`.

```
@own :mut ar1 = [1, 2]
@own ar2 = [3, 4]

add_first!(x, y) = (x[1] += y[1]; nothing)
```

If we set up a lifetime scope manually, we might write:

```julia
@lifetime lt begin
    @ref ~lt :mut ref1 = ar1
    @ref ~lt ref2 = ar2
    add_first!(ref1, ref2)
end
```

However, most of the time you only need to create a lifetime scope for a single function call, so `@bc` lets us do this automatically:

```julia
@bc add_first!(@mut(ar1), ar2)
```

This will evaluate to something that is quite similar to the manual lifetime scope.

`@bc` also supports non-owned variables, which will simply get passed through as-is.

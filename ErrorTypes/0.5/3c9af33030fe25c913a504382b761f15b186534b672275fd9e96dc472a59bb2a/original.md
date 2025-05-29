```
is_ok_and(f, x::Result)::Bool
```

Check if `x` is a result value, and `f(unwrap(x))`. `f(unwrap(x))` must return a `Bool`.

# Examples

```
julia> is_ok_and(isodd, none(Int))
false

julia> is_ok_and(isodd, some(2))
false

julia> is_ok_and(isodd, Result{Int, String}(Ok(9)))
true

julia> is_ok_and(ncodeunits, some("Success!"))
ERROR: TypeError: non-boolean (Int64) used in boolean context
```

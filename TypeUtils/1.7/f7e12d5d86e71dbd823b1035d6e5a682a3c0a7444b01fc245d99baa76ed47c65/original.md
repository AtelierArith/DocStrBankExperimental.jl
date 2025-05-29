```
restructure(T, vals; offset = firstindex(vals) - 1) -> obj::T
```

restructures values `vals[offset+1:offset+n]` into an object `obj` of type `T`. Here `n = struct_length(T)` is the total number of values stored by an object of type `T`.

The default constructors must exist for `T` and, recursively, for any structured fields of `T`.

See also [`destructure`](@ref), [`destructure!`](@ref), and [`struct_length`](@ref).

For an immutable concrete object `obj`, the following identity holds:

```
restructure(typeof(obj), destructure(obj)) === obj
```

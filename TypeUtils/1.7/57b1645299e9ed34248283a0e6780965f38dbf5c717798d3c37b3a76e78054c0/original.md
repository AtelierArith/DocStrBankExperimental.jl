```
destructure!(vals, obj; offset = firstindex(vals) - 1) -> vals
```

destructures object `obj` into `vals[offset+1:offset+n]` and returns `vals`. Here `n = struct_length(obj)` is the total number of values stored by `obj`.

See also [`destructure`](@ref), [`restructure`](@ref), and [`struct_length`](@ref).

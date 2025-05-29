```
@threadsbuffer(specs, ex)
```

Create a [`ThreadsMAllocBuffer`](@ref) object with the given specifications and execute the expression `ex`.

The specifications `specs` can be:

  * `buf(100)` creates a buffer `buf` of type `Float64` with length `100`.
  * `buf(Int, 100)` creates a buffer `buf` of type `Int` with length `100`.
  * `buf(Int, 100, 4)` creates a buffer `buf` of type `Int` with length `100` for `4` threads.

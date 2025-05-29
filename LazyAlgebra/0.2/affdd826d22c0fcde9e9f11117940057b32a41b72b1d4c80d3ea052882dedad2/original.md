```
vcopy!(dst, src) -> dst
```

copies the contents of `src` into `dst` and returns `dst`.  This function checks that the copy makes sense (for instance, for array arguments, the `copyto!` operation does not check that the source and destination have the same dimensions).

Also see [`copyto!`](@ref), [`vcopy`](@ref), [`vswap!`](@ref).

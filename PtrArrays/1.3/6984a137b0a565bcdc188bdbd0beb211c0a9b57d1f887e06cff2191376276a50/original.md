```
free(p::PtrArray)
```

Free the memory allocated by a [`PtrArray`](@ref) allocated by [`malloc`](@ref).

It is only safe to call this function on `PtrArray`s returned by `malloc`, and it is unsafe to perform any operation on a `PtrArray` after calling `free`.

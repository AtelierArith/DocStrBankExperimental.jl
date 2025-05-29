```
witharray_read(f, v::CeedVector, mtype::MemType=MEM_HOST)
```

Same as [`witharray`](@ref), but with read-only access to the data.

# Examples

Display the contents of a vector:

```
witharray_read(display, v)
```

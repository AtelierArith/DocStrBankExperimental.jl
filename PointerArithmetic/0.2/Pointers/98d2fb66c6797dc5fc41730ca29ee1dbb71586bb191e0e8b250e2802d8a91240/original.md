```
shift_start(ptr::Ptr, i::Integer)
```

Shifts the pointer in the specified i number of elements. Another way to call is to use `ptr << nof_elements` Usage:

```julia-repl
julia> a = [1,2,3,4]
julia> pt = Pointer(a)
julia> pt[1]
1
julia> pt = pt << 2
julia> pt[1]
3
```

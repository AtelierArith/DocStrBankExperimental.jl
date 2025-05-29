```
Pointer(arr::AbstractArray)
```

Returns the pointer for the argument array. It also includes auxiliar functions for pointer load and store.

Usage

```julia-repl
julia> a = [1,2,3,4]
julia> pt = Pointer(a)
julia> pt[3]
3
```

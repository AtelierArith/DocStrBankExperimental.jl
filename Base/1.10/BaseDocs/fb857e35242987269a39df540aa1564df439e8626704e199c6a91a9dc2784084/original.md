```
*(x, y...)
```

Multiplication operator. `x*y*z*...` calls this function with all arguments, i.e. `*(x, y, z, ...)`.

# Examples

```jldoctest
julia> 2 * 7 * 8
112

julia> *(2, 7, 8)
112
```

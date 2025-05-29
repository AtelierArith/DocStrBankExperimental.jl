```julia
sigdigits(d)
```

Determine the number of decimal significant figures of a number `d`.

### Examples

```julia
julia> sigdigits(1000)
1

julia> sigdigits(1001)
4

julia> sigdigits(1001.1245)
8
```

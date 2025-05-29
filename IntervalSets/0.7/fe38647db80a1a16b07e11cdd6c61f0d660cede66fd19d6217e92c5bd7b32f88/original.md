```
w = width(iv)
```

Calculate the width (max-min) of interval `iv`. Note that for integers `l` and `r`, `width(l..r) = length(l:r) - 1`.

# Examples

```jldoctest
julia> width(2..7)
5

julia> length(2:7)
6
```

```
flagfirst(iter)
```

An iterator that yields `(isfirst, x)` where `isfirst::Bool` is `true` for the first element, and `false` after that, while the `x`s are elements from `iter`.

```jldoctest
julia> collect(flagfirst(1:3))
3-element Vector{Tuple{Bool, Int64}}:
 (1, 1)
 (0, 2)
 (0, 3)
```

```julia
findnth(t::Collection{Bool}, n::Integer)
```

Return the index of the `n`th true value of `t`, else length(`t`)

### Examples

```julia
julia> t = rand(Bool,5)
5-element Vector{Bool}:
 1
 1
 0
 1
 1

julia> findnth(t, 3)
4
```

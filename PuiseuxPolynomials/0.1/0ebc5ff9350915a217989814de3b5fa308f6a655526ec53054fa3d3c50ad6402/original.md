`variables(p::Mvp)`

`variables(v::AbstractArray)`

returns  the list of variables of `p` (resp. of all `p` in `v`) as a sorted list of `Symbol`s.

```julia-repl
julia> @Mvp x,y,z

julia> variables([z,[y+z],x])
3-element Vector{Symbol}:
 :x
 :y
 :z
```

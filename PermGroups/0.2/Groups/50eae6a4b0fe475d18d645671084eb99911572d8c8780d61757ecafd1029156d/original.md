`Group(l::AbstractVector{T}[,one]) where T`

A  group may be constructed  from a list of  `l` elements of the same type. These  elements must respond to  the functions `*` and  `inv`. If it is not possible  to compute  `one` from  `l` (because  `l[1]` does  not respond to `one`,  or  `l`  is  empty  and  `T`  does  not respond to `one`), then the identity element of the group must be given as a second argument.

```julia-repl
julia> G=Group([[-1 -1;1 0]])
Group([[-1 -1; 1 0]])

julia> elements(G)
3-element Vector{Matrix{Int64}}:
 [1 0; 0 1]
 [-1 -1; 1 0]
 [0 1; -1 -1]
```

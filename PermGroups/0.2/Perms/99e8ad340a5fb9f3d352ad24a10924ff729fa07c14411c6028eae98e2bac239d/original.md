`restricted(p::Perm,domain::AbstractVector{<:Integer})`

`domain` should be a union of orbits of `p`; returns `p` restricted to `domain`

```julia-repl
julia> restricted(Perm(1,2)*Perm(3,4),3:4)
(3,4)
```

`restricted(p::Perm,domain::AbstractVector{<:Integer})`

`domain` は `p` の軌道の和であるべきです; `domain` に制限された `p` を返します。

```julia-repl
julia> restricted(Perm(1,2)*Perm(3,4),3:4)
(3,4)
```

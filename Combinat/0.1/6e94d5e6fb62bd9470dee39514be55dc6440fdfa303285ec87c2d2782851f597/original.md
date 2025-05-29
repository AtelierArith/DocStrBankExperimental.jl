`primitiveroot(m::Integer)`   a   primitive   root,   that   is  generating multiplicatively  `mod.  m`  the  `prime_residues(m)`. The function returns `nothing` if there is no primitive root `mod. m`.

A  primitive root exists if `m` is euqal to `4` or `p^a` or `2p^a` for `p` prime>2.

```julia-repl
julia> primitiveroot(23)
5
```

`graph_automorphisms(t::Vector{TypeIrred})`

Given  the `refltype` of a  finite Coxeter group, returns  the group of all Graph automorphisms of `t` as a group of permutations of `indices(t)`.

```julia-repl
julia> W=coxgroup(:D,4)
D₄

julia> graph_automorphisms(refltype(W*W))
Group((1,5)(2,6)(3,7)(4,8),(1,2),(1,4))
```

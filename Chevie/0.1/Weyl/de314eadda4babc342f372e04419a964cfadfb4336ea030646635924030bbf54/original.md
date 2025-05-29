`describe_involution(W,w)`

Given  an  involution  `w`  of  a  Coxeter  group  `W`,  by  a  theorem  of [Richardson1982](biblio.htm#rich82)  there is  a unique  parabolic subgroup `P`  of `W` such that `P` is finite  and `w` is the longest element of `P`, and is central in `P`. The function returns `I` such that `P==reflection_subgroup(W,I)` and `w==longest(reflection_subgroup(W,I))`.

```julia-repl
julia> W=coxgroup(:A,2)
A₂

julia> w=longest(W)
(1,5)(2,4)(3,6)

julia> describe_involution(W,w)
1-element Vector{Int64}:
 3

julia> w==longest(reflection_subgroup(W,[3]))
true
```

For now only works for finite Coxeter groups.

`word(W::CoxeterGroup,w)`

returns  a reduced word in the standard generators of the Coxeter group `W` for  the  element  `w`  (represented  as  the  vector  of the corresponding generator indices).

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> w=perm"(1,11)(3,10)(4,9)(5,7)(6,12)"
(1,11)(3,10)(4,9)(5,7)(6,12)

julia> w in W
true

julia> word(W,w)
5-element Vector{Int64}:
 1
 2
 3
 2
 1
```

The  result  of   `word`  is  the  lexicographically  smallest reduced word for `w` (for the ordering of the Coxeter generators given by `gens(W)`).

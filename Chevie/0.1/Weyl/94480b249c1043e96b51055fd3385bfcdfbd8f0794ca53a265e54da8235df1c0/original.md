`highest_short_root(W)`

It  is  an  error  if  `W`  is  not an irreducible Coxeter group. Otherwise `HighestShortRoot`  returns the index  of the unique  short root of maximal height  of `W`. If all roots have the same length then this is the index of the unique root of maximal height, equal to `nref(W)`.

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> highest_short_root(W)
4
```

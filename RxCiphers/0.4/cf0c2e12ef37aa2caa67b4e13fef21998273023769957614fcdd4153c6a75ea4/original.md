```
^(W::NCharSpace{1}, n::Int) -> NCharSpace{n}
```

Returns a composite version of `W`, encoding substrings made of `n` unit substrings to single tokens.

# Examples

```julia-repl
julia> Decimal
10-element CharSpace:
["0", "1", "2", "3", "4", "5", "6", "7", "8", "9"]

julia> W = Decimal^2
100-element 2-char CharSpace:
["0", "1", "2", "3", "4", "5", "6", "7", "8", "9"]

julia> tokenise.(["1", "2"], Ref(Decimal))
2-element Vector{Int64}:
 2
 3

julia> W.linear[2,3]
22

julia> W.charmap[22]
"12"
```

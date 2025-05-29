`Lusztigaw(W,w)`

For  `w` an element  of the Coxeter  groups `W`, this  function returns the coefficients  on the irreducible characters of the virtual Character `ca_w` defined  in [5.10.2 Lusztig1985](biblio.htm#Lus85).  This character has the property that the corresponding almost character is integral and positive.

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> l=Lusztigaw(W,W(1))
6-element Vector{Int64}:
 0
 0
 1
 0
 1
 1

julia> sum(l.*map(i->almostchar(W,i),eachindex(l)))
[G₂]:<φ′₁‚₃>+<φ₂‚₁>+<φ₂‚₂>
```

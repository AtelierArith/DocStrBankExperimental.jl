`conjugate(p,conjugation)`

This program modifies a presentation by conjugating a generator by another. The  conjugation to  apply is  described by  a length-3  string of the same style  as  the  result  of  `display_balanced`,  that is `"abA"` means replace  the second generator by its  conjugate by the first, and  `"Aba"` means replace it by its conjugate by the inverse of the first.

```julia-rep1
julia> display_balanced(P)
1: dabcd=abcda
2: dabcdb=cabcda
3: bcdabcd=dabcdbc

julia> display_balanced(conjugate(P,"Cdc"))
<< presentation with 4 generators, 3 relators of total length 36>>
1: dcabdc=cabdca
2: abdcab=cabdca
3: bdcabd=cabdca
```

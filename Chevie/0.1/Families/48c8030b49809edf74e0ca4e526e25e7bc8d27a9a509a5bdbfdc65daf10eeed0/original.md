`ndrinfeld_double(g)`

This  function returns the number of elements that the family associated to the  Drinfeld double of the group `g` would have, without computing it. The evident advantage is the speed.

```julia-repl
julia> Families.ndrinfeld_double(complex_reflection_group(5))
378
```

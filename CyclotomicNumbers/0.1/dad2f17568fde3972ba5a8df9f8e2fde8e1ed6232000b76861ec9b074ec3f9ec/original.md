`Root1(c)`

`c`  should  be  a  `Cyc`,  a  `Real`,  or  a `Complex`. `Root1(c)` returns `E(n,e)`  if `c==E(n,e)`, and  `nothing` if `c`  is not equal  to a root of unity.

```julia-repl
julia> r=Root1(-E(9,2)-E(9,5))
Root1: ζ₉⁸

julia> order(r)
9

julia> exponent(r)
8

julia> Cyc(r) # the Zumbroich normal form is a sum of 2 roots of unity
Cyc{Int64}: -ζ₉²-ζ₉⁵

julia> Root1(-E(9,4)-E(9,5)) # nothing
```

`all_ge_1(M::Matrix;approx=x->x)`

This  function determines if a list of real linear forms represented by the rows  of a  matrix `M`  can be  made simultaneously  `≥1`. The  result is a vector  `v` such  that `all(≥(1),M*v)`,  or `nothing`  if there  is no such vector.

`approx(x)`  is a  function giving  an approximate  real value for `x`. For instance,  setting `approx=Float64` enables to  use this function with real `Cyc` numbers.

```julia-repl
julia> all_ge_1([1 1 -1;1 -1 1;-1 1 1])
3-element Vector{Float64}:
 1.0
 1.0
 1.0
```

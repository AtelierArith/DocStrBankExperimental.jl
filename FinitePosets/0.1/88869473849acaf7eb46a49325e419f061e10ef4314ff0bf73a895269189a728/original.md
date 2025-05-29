`ranking(P)`

here `P` is a `Poset` or a `CPoset`. A poset is ranked if the recipe

`ρ(x)=0` if `x∈minima(P)`, `ρ(y)=ρ(x)+1` if `y` is an immediate successor of `x`

gives a well-defined function `ρ`. Then `ρ` is called a ranking of `P`. The function  `ranking` returns the  vector of `ρ(x)`  for `x` running over the elements of `P` if `P` has a ranking, and `nothing` otherwise.

A  poset  `P`  is  graded  if  all  maximal chains have the same length, or equivalently `P` is ranked and `allequal(ranking(P)[maxima(P)])`.

```julia-repl
julia> ranking(Poset(:partitionsdominance,6))
11-element Vector{Int64}:
 0
 1
 2
 3
 3
 4
 5
 5
 6
 7
 8

julia> ranking(Poset(:partitionsdominance,7)) # not ranked

```

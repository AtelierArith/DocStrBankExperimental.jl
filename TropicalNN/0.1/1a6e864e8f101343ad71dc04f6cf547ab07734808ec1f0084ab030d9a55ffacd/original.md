```
TropicalPuiseuxPoly(coeff::Dict, exp::Vector{Vector{T}}, sorted::Bool)
```

Constructs a tropical Puiseux polynomial from a vector of coefficients and a vector of exponents, by first sorting the exponents lexicographically, and then constructing the dictionary of coefficients.

```jldoctest
julia> f = TropicalPuiseuxPoly([1, 2], [[1, 2], [2, 1]])
  TropicalPuiseuxPoly{Int64}(Dict([2, 1] => 2, [1, 2] => 1), [[1, 2], [2, 1]])
```

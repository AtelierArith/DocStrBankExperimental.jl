`Pol(x::AbstractVector,y::AbstractVector)`

Interpolation:  find a `Pol` (of  nonnegative valuation) of smallest degree taking  values `y` at points  `x`. The values `y`  should be in a field for the function to be type stable.

```julia-repl
julia> p=Pol([1,1,1])
Pol{Int64}: q²+q+1

julia> vals=p.(1:5)
5-element Vector{Int64}:
  3
  7
 13
 21
 31

julia> Pol(1:5,vals*1//1)
Pol{Rational{Int64}}: q²+q+1

julia> Pol(1:5,vals*1.0)
Pol{Float64}: 1.0q²+1.0q+1.0
```

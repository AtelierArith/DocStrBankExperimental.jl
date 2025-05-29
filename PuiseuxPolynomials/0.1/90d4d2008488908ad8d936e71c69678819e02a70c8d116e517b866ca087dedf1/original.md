`degree(m::Mvp[,v::Symbol])`

The `degree` of a monomial is the sum of  the exponents of the variables. The `degree` of an `Mvp` is the largest degree of a monomial.

With  second argument a  variable name, `degree`  returns the degree of the polynomial in that variable.

```julia-repl
julia> a=x^2+x*y
Mvp{Int64}: x²+xy

julia> degree(a), degree(a,:y), degree(a,:x)
(2, 1, 2)
```

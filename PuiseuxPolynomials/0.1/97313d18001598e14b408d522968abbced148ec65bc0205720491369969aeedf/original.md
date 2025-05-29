`valuation(m::Mvp[,v::Symbol])`

The `valuation` of an `Mvp` is the minimal degree of a monomial.

With  second argument a variable name, `valuation` returns the valuation of the polynomial in that variable.

```julia-repl
julia> @Mvp x,y; a=x^2+x*y
Mvp{Int64}: x²+xy

julia> valuation(a), valuation(a,:y), valuation(a,:x)
(2, 0, 1)
```

`Pol(p::Mvp,v::Symbol)`

returns  a polynomial whose coefficients are  the coefficients of the `Mvp` `p`  with respect to the variable `v`  (as `Mvp`s). The variable `v` should appear only with integral powers in `p`.

```julia-repl
julia> p=(x+y^(1//2))^3
Mvp{Int64,Rational{Int64}}: x³+3x²y½+3xy+y³⁄₂

julia> Pol(:q); Pol(p,:x)
Pol{Mvp{Int64, Rational{Int64}}}: q³+3y½q²+3yq+y³⁄₂
```

This  can be used for instance to  compute the discriminant of a polynomial with respect to one of its variables:

```julia-repl
julia> p=x+y^2+x^3+y^3
Mvp{Int64}: x³+x+y³+y²

julia> discriminant(Pol(p,:x))
Mvp{Int64}: 27y⁶+54y⁵+27y⁴+4
```

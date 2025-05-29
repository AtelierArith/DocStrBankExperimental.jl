  * `fraction(b::GarsideElt)`
  * `denominator(b::GarsideElt)`
  * `numerator(b::GarsideElt)`

`fraction(b)`  returns a  tuple `(x,y)`  of positive  Garside elements with trivial  `leftgcd`  and  such  that  `b=x\y`.  For  such  a decomposition, `denominator(b)` returns `x` and `numerator(b)` returns `y`.

```julia-repl
julia> B=BraidMonoid(coxgroup(:A,3))
BraidMonoid(A₃)

julia> b=B( 2, 1, -3, 1, 1)
(23)⁻¹321.1.1

julia> fraction(b)
(23, 321.1.1)
```

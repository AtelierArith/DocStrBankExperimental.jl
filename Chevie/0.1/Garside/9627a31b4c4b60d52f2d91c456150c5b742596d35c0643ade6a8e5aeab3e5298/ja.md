  * `fraction(b::GarsideElt)`
  * `denominator(b::GarsideElt)`
  * `numerator(b::GarsideElt)`

`fraction(b)` は、トリビアルな `leftgcd` を持つ正のガーサイド要素のタプル `(x,y)` を返し、`b=x\y` となります。そのような分解に対して、`denominator(b)` は `x` を返し、`numerator(b)` は `y` を返します。

```julia-repl
julia> B=BraidMonoid(coxgroup(:A,3))
BraidMonoid(A₃)

julia> b=B( 2, 1, -3, 1, 1)
(23)⁻¹321.1.1

julia> fraction(b)
(23, 321.1.1)
```

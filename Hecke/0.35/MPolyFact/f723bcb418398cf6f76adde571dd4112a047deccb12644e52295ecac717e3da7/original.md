```
factor_absolute(f::QQMPolyRingElem)
```

Compute the factorisation of f in Q[X] over C, returns an array with first component the leading coefficient, and then, for each irreducible factor over Q[X] a pair, containing

  * a tuple with

      * an irreducible factor over a number field
      * the product of all the other conjugate factors over this field
  * the multiplicity.

Recall that for each irreducible over Q there is one (minimal) number field (possibly Q) where this factor splits further. In this case all the factor over this field are Galois-conjugate. In order to not create a huge splitting field, only one factor and the product of the conjugates is returned.

# Examples

```julia
julia> Qx, (x, y) = polynomial_ring(QQ, ["x", "y"]);

julia> f = (x^3+5*y^3)*(x^2+2*y^2);

julia> z = factor_absolute(f)

3-element Vector{Any}:
                                                                            1
                AbstractAlgebra.Generic.MPoly{AbsSimpleNumFieldElem}[x + _a*y, x - _a*y] => 1
 AbstractAlgebra.Generic.MPoly{AbsSimpleNumFieldElem}[x + _a*y, x^2 - _a*x*y + _a^2*y^2] => 1

julia> z[2][1][1]
x + _a*y

julia> base_ring(ans)
Number field over Rational Field with defining polynomial x^2 + 2

julia> base_ring(z[3][1][1])
Number field over Rational Field with defining polynomial x^3 - 5
```

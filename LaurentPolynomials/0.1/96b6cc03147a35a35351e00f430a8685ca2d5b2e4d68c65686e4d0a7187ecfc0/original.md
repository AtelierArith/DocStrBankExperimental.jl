This  package  implements  univariate  Laurent  polynomials, and univariate rational  fractions. The  coefficients can  be in  any ring  (possibly even non-commutative, like `Matrix{Int}).

The  initial  motivation  in  2018  was  to  have  an  easy way to port GAP polynomials  to  Julia.  The  reasons  for  still having my own package are multiple:

  * I need my  polynomials to  behave  well  when the coefficients are in a ring,  in which  case I use pseudo-division and subresultant gcd.
  * I need my polynomials to  work as well as possible with coefficients of type  `T` where the elements  have a `zero` method  but `T` itself does not  have one, because `T` does  not contain the necessary information. An  example is modular arithmetic with  a `BigInt` modulus which cannot be  part of the  type. For this  reason the `zero`  polynomial does not have  an empty list of coefficients,  but a  list containing an element equal  to zero, so it is  always possible to get a  zero of type T from the zero polynomial.
  * `LaurentPolynomials` is designed to be used by `PuiseuxPolynomials`.
  * Often  my polynomials  are several  times  faster  than  those  in  the `Polynomials`  package.  In  addition,  the  interface  is  simple  and flexible.

The  only package this  package depends on  is `LinearAlgebra`, through the use of the `exactdiv` function.

Laurent  polynomials are of  the parametric type  `Pol{T}`, where `T`is the type  of  the  coefficients.  They  are  constructed  by giving a vector of coefficients  of  type  `T`,  and  a  valuation  (an  `Int`).  We call true polynomials those whose valuation is `≥0`.

There  is  a  current  variable  name  (a  `Symbol`) which is used to print polynomials  nicely at  the repl  or in  IJulia or  Pluto. This name can be changed  globally,  or  just  for  printing a specific polynomial. However, polynomials  do not individually record which symbol they should be printed with.

# Examples

```julia-repl
julia> Pol(:q) # define symbol used for printing and return Pol([1],1)
Pol{Int64}: q

julia> @Pol q  # same as q=Pol(:q)  useful to start session with polynomials
Pol{Int64}: q

julia> Pol([1,2]) # valuation is taken to be 0 if omitted
Pol{Int64}: 2q+1

julia> 2q+1       # same polynomial
Pol{Int64}: 2q+1

julia> Pol()   # omitting all arguments gives Pol([1],1)
Pol{Int64}: q

julia> p=Pol([1,2,1],-1) # here the valuation is specified to be -1
Pol{Int64}: q+2+q⁻¹

julia> q+2+q^-1 # same polynomial
Pol{Int64}: q+2+q⁻¹
```

```julia-rep1
julia> print(p) # if not nice printing give an output which can be read back
Pol([1, 2, 1],-1)

# change the variable for printing just this time
julia> print(IOContext(stdout,:limit=>true,:varname=>"x"),p)
x+2+x⁻¹

julia> print(IOContext(stdout,:TeX=>true),p) # TeXable output (used in Pluto, IJulia)
q+2+q^{-1}
```

A  polynomial can be  taken apart with  the functions `valuation`, `degree` and  `getindex`. An index  `p[i]` returns the  coefficient of degree `i` of `p`.

```julia-repl
julia> valuation(p),degree(p)
(-1, 1)

julia> p[0], p[1], p[-1], p[10]
(2, 1, 1, 0)

julia> p[valuation(p):degree(p)]
3-element Vector{Int64}:
 1
 2
 1

julia> p[begin:end]  # the same as the above line
3-element Vector{Int64}:
 1
 2
 1

julia> coefficients(p)  # the same again
3-element Vector{Int64}:
 1
 2
 1
```

The coefficients can come from any ring:

```julia-repl
julia> h=Pol([[1 1;0 1],[1 0; 0 1]])
Pol{Matrix{Int64}}: [1 0; 0 1]q+[1 1; 0 1]

julia> h^3
Pol{Matrix{Int64}}: [1 0; 0 1]q³+[3 3; 0 3]q²+[3 6; 0 3]q+[1 3; 0 1]
```

A  polynomial  is  a  *scalar*  if  its  valuation  and degree are `0`. The `scalar` function  returns the constant coefficient  if the polynomial is a scalar, and `nothing` otherwise.

```julia-repl
julia> Pol(1)
Pol{Int64}: 1

julia> convert(Pol{Int},1) # the same thing
Pol{Int64}: 1

julia> scalar(Pol(1))
1

julia> convert(Int,Pol(1)) # the same thing
1

julia> Int(Pol(1))         # the same thing
1

julia> scalar(q+1) # nothing; convert would give an error
```

In arrays `Pol{T}` of different types `T` are promoted to the same type `T` (if  the  `T`  involved  have  a  promotion)  and a number is promoted to a polynomial.

Usual  arithmetic (`+`, `-`,  `*`, `^`, `/`,  `//`, `one`, `isone`, `zero`, `iszero`,  `==`) works. Elements  of type `<:Number`  or of type  `T` for a `Pol{T}`   are  considered  as   scalars  for  scalar   operations  on  the coefficients.

```julia-repl
julia> derivative(p)
Pol{Int64}: 1-q⁻²

julia> p=(q+1)^2
Pol{Int64}: q²+2q+1

julia> p/2
Pol{Float64}: 0.5q²+1.0q+0.5

julia> p//2
Pol{Rational{Int64}}: (1//2)q²+q+1//2

julia> p(1//2) # value of p at 1//2
9//4

julia> p(0.5)
2.25

julia> Pol([1,2,3],[2.0,1.0,3.0])  # find p taking values [2.0,1.0,3.0] at [1,2,3]
Pol{Float64}: 1.5q²-5.5q+6.0
```

Polynomials  are scalars  for broadcasting.  They can  be sorted (they have `cmp`   and  `isless`  functions  which   compare  the  valuation  and  the coefficients), they can be keys in a `Dict` (they have a `hash` function).

The  functions  `divrem`,  `div`,  `%`,  `gcd`,  `gcdx`,  `lcm`, `powermod` operate  between  true  polynomials  over  a  field,  using  the polynomial division.  Over a ring it is better  to use `pseudodiv` and `srgcd` instead of  `divrem`  and  `gcd`  (by  default  `gcd`  between  integer polynomials delegates to `srgcd`).

`LinearAlgebra.exactdiv`  does division (over a field or a ring) when it is exact, otherwise gives an error.

```julia-repl
julia> divrem(q^3+1,2q+1) # changes coefficients to field elements
(0.5q²-0.25q+0.125, 0.875)

julia> divrem(q^3+1,2q+1//1) # case of coefficients already field elements
((1//2)q²+(-1//4)q+1//8, 7//8)

julia> pseudodiv(q^3+1,2q+1) # pseudo-division keeps the ring
(4q²-2q+1, 7)

julia> (4q^2-2q+1)*(2q+1)+7 # but multiplying back gives a multiple of the polynomial
Pol{Int64}: 8q³+8

julia> LinearAlgebra.exactdiv(q+1,2.0) # LinearAlgebra.exactdiv(q+1,2) would give an error
Pol{Float64}: 0.5q+0.5
```

Finally,   `Pol`s  have   methods  `conj`,   `adjoint`  which   operate  on coefficients,  methods `positive_part`,  `negative_part` and  `bar` (useful for  Kazhdan-Lusztig  theory)  and  a  method  `randpol`  to produce random polynomials.

Inverting  polynomials is a way to  get a rational fraction `Frac{Pol{T}}`, where  `Frac`  is  a  general  type  for  fractions. Rational fractions are normalised  so that the numerator and denominator are true polynomials that are  prime to each  other. They have  the arithmetic operations  `+`, `-` , `*`,  `/`, `//`,  `^`, `inv`,  `one`, `isone`,  `zero`, `iszero` (which can operate between a `Pol` or a `Number` and a `Frac{Pol{T}}`).

```julia-repl
julia> a=1/(q+1)
Frac{Pol{Int64}}: 1/(q+1)

julia> Pol(2/a) # convert back to `Pol`
Pol{Int64}: 2q+2

julia> numerator(a)
Pol{Int64}: 1

julia> denominator(a)
Pol{Int64}: q+1

julia> m=[q+1 q+2;q-2 q-3]
2×2 Matrix{Pol{Int64}}:
 q+1  q+2
 q-2  q-3

julia> n=inv(Frac.(m)) # convert to rational fractions to invert the matrix
2×2 Matrix{Frac{Pol{Int64}}}:
 (-q+3)/(2q-1)  (-q-2)/(-2q+1)
 (q-2)/(2q-1)   (q+1)/(-2q+1)

julia> map(x->x(1),n) # evaluate at 1 the inverse matrix
2×2 Matrix{Float64}:
  2.0   3.0
 -1.0  -2.0

julia> map(x->x(1;Rational=true),n) # evaluate at 1 using //
2×2 Matrix{Rational{Int64}}:
  2   3
 -1  -2
```

Rational fractions are also scalars for broadcasting and can be sorted (have `cmp` and `isless` methods).

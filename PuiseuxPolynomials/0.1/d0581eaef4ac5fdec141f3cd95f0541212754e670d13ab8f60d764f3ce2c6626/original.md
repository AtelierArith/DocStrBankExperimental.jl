This  package implements  Puiseux polynomials,  that is linear combinations with  coefficients  of  some  type  `C`  of monomials of the type `x₁^{a₁}… xₙ^{aₙ}`  where  `xᵢ`  are  variables  and  `aᵢ` are exponents which can be arbitrary  rational  numbers.  When  the  `aᵢ`  are  integers  we  speak of "multivariate Laurent polynomials", and when the `aᵢ` are positive integers we speak of "multivariate polynomials" (or true polynomials).

This  package also implements  multivariate rational fractions, constructed as  the quotient of two Laurent polynomials  (which is normalised to be the quotient  of  two  true  polynomials).  In  particular,  this  package is a perfectly  usable (and hopefully quite good) implementation of multivariate polynomials  and multivariate rational  fractions, if that  is what you are interested in.

The main use of Puiseux polynomials is that, if the elements of `C` form an algebraically  closed field, they are the ring of integers of the algebraic closure   of  the  the  multivariate   rational  fractions.  In  particular cyclotomic  Hecke algebras take their  character values and representations in them.

This  package depends only on the packages `Reexport`, `LaurentPolynomials` and `ModuleElts`s; the names defined by `LaurentPolynomials` are reexported by this package.

Our  Puiseux polynomials have  the parametric type  `Mvp{C,E}` where `C` is the  type of the coefficients and `E` is the type of the exponents: `E=Int` for   Laurent  polynomials;  `E=Rational{Int}`  for  more  general  Puiseux polynomials.  When printing the  type of an  `Mvp`, only `C`  is printed if `E==Int`.  Rational  fractions  are  only  defined  if  the  numerator  and denominator  are true  polynomials; they  have type `Frac{Mvp{C,Int}}`. The quotient of two Laurent polynomials is normalised to a quotient of two true polynomials.

We first look at how to make Puiseux polynomials.

`@Mvp x₁,…,xₙ`

assigns  to each  Julia name  `xᵢ` an  `Mvp` representing  an indeterminate suitable   to  build   multivariate  polynomials   or  rational  fractions. `Mvp(:x₁)` creates the same `Mvp` without assigning it to variable `x₁`.

```julia-repl
julia> @Mvp x,y # creates the variables x,y

julia> (x+y^-1)^3
Mvp{Int64}: x³+3x²y⁻¹+3xy⁻²+y⁻³

julia> x+Mvp(:z)
Mvp{Int64}: x+z

julia> x^(1//2)  # a Puiseux monomial
Mvp{Int64,Rational{Int64}}: x½

julia> Mvp(3)  # convert a number to an Mvp with only a constant term
Mvp{Int64}: 3
```

It  is convenient  to create  `Mvp`s using  variables like `x,y` above. The functions  `repr` or `print`  display an `Mvp`  in a form  that can be read back  in Julia –  this is also  the way an  `Mvp` is printed  in a context other than the repl, IJulia or pluto:

```julia-repl
julia> repr(3x*y^-2+4)
"Mvp{Int64, Int64}([:x=>1,:y=>-2]=>3,[]=>4)"
```

It  is better not to use this  form casually, since the arguments *must* be normalized (sorted by key, and no duplicate key).

Only  monomials and one-term `Mvp`s can  be raised to a non-integral power; the  `Mvp` with one term constant `c`  times the monomial `m` can be raised to  a fractional  power of  denominator `d`  if and  only if `root(c,d)` is defined (this is equivalent to `c^{1//d}` for floats);

```julia-repl
julia> (4x)^(1//2)
Mvp{Int64,Rational{Int64}}: 2x½

julia> (2.0x)^(1//2)
Mvp{Float64,Rational{Int64}}: 1.4142135623730951x½

julia> root(2.0x)
Mvp{Float64,Rational{Int64}}: 1.4142135623730951x½
```

One  may  want  to  define  `root`  differently;  for instance, in my other package   `CylotomicNumbers`  I   define  square   roots  of  rationals  as cyclotomics, and I also have implemented arbitrary roots of roots of unity.

```julia-rep1
julia> using CyclotomicNumbers

julia> (2x)^(1//2)
Mvp{Cyc{Int64},Rational{Int64}}: √2x½

julia> (E(3)*x)^(2//3)
Mvp{Cyc{Int64},Rational{Int64}}: ζ₉²x⅔
```

There  are various ways to take an  `Mvp` apart. Below are the most direct; look   also  at  the   functions  `coefficient`,  `coefficients`,  `pairs`, `monomials`, `variables` and `powers`.

```julia-repl
julia> p=3x*y^-2+4
Mvp{Int64}: 3xy⁻²+4

julia> term(p,1) # a term is a Pair monomial=>coefficient
xy⁻² => 3

julia> term(p,2) # the trivial monomial Monomial() prints as an empty string
 => 4

julia> length(p) # the number of terms
2

julia> term.(p,1:length(p)) # same as pairs(p)
2-element Vector{Pair{Monomial{Int64}, Int64}}:
 xy⁻² => 3
      => 4

julia> last(term(p,1)) # same as first(coefficients(p))
3

julia> m=first(term(p,1)) # same as first(monomials(p))
Monomial{Int64}:xy⁻²

julia> length(m) # how many variables in m
2

julia> map((x,y)->x=>y,variables(m),powers(m)) # same as pairs(m)
2-element Vector{Pair{Symbol, Int64}}:
 :x => 1
 :y => -2

julia> degree(m,:x) # power of x in m
1

julia> degree(m,:y) # power of y in m
-2
```

The valuation and degree of an Mvp can be inspected globally or variable by variable.

```julia-repl
julia> p
Mvp{Int64}: 3xy⁻²+4

julia> variables(p)
2-element Vector{Symbol}:
 :x
 :y

julia> degree(p),degree(p,:x),degree(p,:y)
(0, 1, 0)

julia> valuation(p),valuation(p,:x),valuation(p,:y)
(-1, 0, -2)
```

The  terms in an  `Mvp` are ordered  by a monomial  order (that is, a total order  on  monomials  such  that  `x<y`  implies  `xz<yz` for any monomials `x,y,z`).  The terms are in descending order, so that the first term is the highest.  The default order is `lex`.  The orders `grlex` and `grevlex` are also  implemented (see their docstrings and  `grobner_basis` for how to use them).

An `Mvp` is a *scalar* if the valuation and degree are `0` (it has a single term  corresponding to the  `one` monomial). The  function `scalar` returns the constant coefficient if the `Mvp` is a scalar, and `nothing` otherwise.

Usual  arithmetic (`+`, `-`,  `*`, `^`, `/`,  `//`, `one`, `isone`, `zero`, `iszero`,  `==`)  works.  Elements  of  type  `<:Number`  are considered as scalars for scalar multiplication or division of the coefficients.

```julia-repl
julia> p
Mvp{Int64}: 3xy⁻²+4

julia> p^2
Mvp{Int64}: 9x²y⁻⁴+24xy⁻²+16

julia> p/2
Mvp{Float64}: 1.5xy⁻²+2.0

julia> p//2
Mvp{Rational{Int64}}: (3//2)xy⁻²+2//1
```

When  converting an `Mvp` to another type of `Mvp` one needs to specify the two  type parameters  (the type  of the  coefficients and  the type  of the exponents).

```julia-repl
julia> Mvp{Float64,Rational{Int}}(p)
Mvp{Float64,Rational{Int64}}: 3.0xy⁻²+4.0
```

One  can evaluate an `Mvp`,  setting the value of  some variables, by using the  function call syntax. 

```julia-repl
julia> p=x+y
Mvp{Int64}: x+y

julia> p(x=2)    # evaluate p at x=2
Mvp{Int64}: y+2

julia> value(p,:x=>2) # there is also a more explicit `value` function.
Mvp{Int64}: y+2

julia> p(x=2,y=x) # simultaneous evaluation
Mvp{Int64}: x+2

julia> value(p,:x=>2,:y=>x)
Mvp{Int64}: x+2
```

Note  that  an  `Mvp`  always  evaluates  to an `Mvp`, for consistency. You should  use `scalar` on the  result of giving values  to all variables in a `Mvp` to get a number.

```julia-repl
julia> p(x=1,y=2)
Mvp{Int64}: 3

julia> scalar(p(x=1,y=2))
3

julia> v=(x^(1//2))(x=2.0)
Mvp{Float64,Rational{Int64}}: 1.4142135623730951

julia> scalar(v)
1.4142135623730951
```

One  can divide an `Mvp` by another when the division is exact, compute the `gcd` and `lcm` of two `Mvp`.

```julia-repl
julia> LinearAlgebra.exactdiv(x^2-y^2,x-y) # errors if the division is not exact
Mvp{Int64}: x+y

julia> (x+y)/(2x^2)   # divide by a monomial
Mvp{Float64}: 0.5x⁻¹+0.5x⁻²y

julia> (x+y)//(2x^2)
Mvp{Rational{Int64}}: (1//2)x⁻¹+(1//2)x⁻²y

julia> (x+y)/(x-y)   # if the division is not exact one gets a rational fraction
Frac{Mvp{Int64, Int64}}: (x+y)/(x-y)
```

Raising  a non-monomial  Laurent polynomial  to a  negative power returns a rational   fraction.  Rational  fractions  are  normalized  such  that  the numerator  and denominators are true polynomials  prime to each other. They have  the  arithmetic  operations  `+`,  `-`  , `*`, `/`, `//`, `^`, `inv`, `one`,  `isone`, `zero`, `iszero` (these  operations can operate between an `Mvp` or a `Number` and a `Frac{<:Mvp}`).

```julia-repl
julia> (x+1)^-2
Frac{Mvp{Int64, Int64}}: 1/(x²+2x+1)

julia> x+1/(y+1)
Frac{Mvp{Int64, Int64}}: (xy+x+1)/(y+1)

julia> 1/(y-1)-1/(y+1)
Frac{Mvp{Int64, Int64}}: 2/(y²-1)
```

One  can evaluate a `Frac`,  setting the value of  some variables, by using the function call syntax or the `value` function:

```julia-repl
julia> ((x+y)/(x-y))(x=y+1)
Mvp{Float64}: 2.0y+1.0

julia> value((x+y)/(x-y),:x=>y+1;Rational=true) # Rational=true says use //
Mvp{Int64}: 2y+1
```

A  `Frac` can be dissected using `numerator` and `denominator`. `Frac`s and `Mvp`s  are  scalars  for  broadcasting  and  can be sorted (have `cmp` and `isless` methods).

```julia-repl
julia> m=[x+y x-y;x+1 y+1]
2×2 Matrix{Mvp{Int64, Int64}}:
 x+y  x-y
 x+1  y+1

julia> n=inv(Frac.(m))
2×2 Matrix{Frac{Mvp{Int64, Int64}}}:
 (-y-1)/(x²-2xy-y²-2y)  (x-y)/(x²-2xy-y²-2y)
 (x+1)/(x²-2xy-y²-2y)   (-x-y)/(x²-2xy-y²-2y)

julia> lcm(denominator.(n))
Mvp{Int64}: x²-2xy-y²-2y
```

Finally,   `Mvp`s  have   methods  `conj`,   `adjoint`  which   operate  on coefficients,   a   `derivative`   method,   and  methods  `positive_part`, `negative_part` and `bar` (useful for Kazhdan-Lusztig theory).

```julia_repl
julia> @Mvp z
Mvp{Int64}: z

julia> hessian(p,vars)=[derivative(derivative(p,x),y) for x in vars, y in vars]
hessian (generic function with 1 method)

julia> hessian(x^2*y^2*z^2,[:x,:y,:z])
3×3 Matrix{Mvp{Int64, Int64}}:
 2y²z²  4xyz²  4xy²z
 4xyz²  2x²z²  4x²yz
 4xy²z  4x²yz  2x²y²

julia> jacobian(pols,vars)=[derivative(p,v) for p in pols, v in vars]
jacobian (generic function with 1 method)

julia> jacobian([x,y,z],[:x,:y,:z])
3×3 Matrix{Mvp{Int64, Int64}}:
 1  0  0
 0  1  0
 0  0  1

julia> p=(x+y^-1)^4
Mvp{Int64}: x⁴+4x³y⁻¹+6x²y⁻²+4xy⁻³+y⁻⁴

julia> positive_part(p)
Mvp{Int64}: x⁴

julia> negative_part(p)
Mvp{Int64}: y⁻⁴

julia> bar(p)
Mvp{Int64}: y⁴+4x⁻¹y³+6x⁻²y²+4x⁻³y+x⁻⁴
```

Despite  the degree of generality of our  polynomials, the speed is not too shabby.  For the Fateman test f(f+1)  where f=(1+x+y+z+t)^15, we take 3sec. According to the Nemo paper, Sagemath takes 10sec and Nemo takes 1.6sec.

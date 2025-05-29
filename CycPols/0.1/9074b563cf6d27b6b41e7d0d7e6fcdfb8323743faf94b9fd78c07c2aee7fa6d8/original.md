This package deals with products of Cyclotomic polynomials.

Cyclotomic  numbers, and cyclotomic polynomials  over the rationals or some cyclotomic  field, are important in the theories of finite reductive groups and  Spetses. In particular Schur elements of cyclotomic Hecke algebras are products of cyclotomic polynomials.

The  type  `CycPol`  represents  the  product  of  a `coeff` (a constant, a polynomial or a rational fraction in one variable) with a rational fraction in  one variable with all poles or zeroes equal to 0 or roots of unity. The advantages  of  representing  as  `CycPol`  such  objects are: nice display (factorized),  less storage, fast  multiplication, division and evaluation. The drawback is that addition and subtraction are not implemented!

This   package  uses   the  polynomials   `Pol`  defined   by  the  package `LaurentPolynomials`  and  the  cyclotomic  numbers  `Cyc`  defined  by the package `CyclotomicNumbers`.

The  method  `CycPol(a::Pol)`  converts  `a`  to  a `CycPol` by finding the largest  cyclotomic polynomial  dividing, leaving  a `Pol` `coefficient` if some roots of the polynomial are not roots of unity.

```julia-repl
julia> using LaurentPolynomials

julia> @Pol q
Pol{Int64}: q

julia> p=CycPol(q^25-q^24-2q^23-q^2+q+2) # a `Pol` coefficient remains
(q-2)Φ₁Φ₂Φ₂₃

julia> p(q) # evaluate CycPol p at q
Pol{Int64}: q²⁵-q²⁴-2q²³-q²+q+2

julia> p*inv(CycPol(q^2+q+1)) # `*`, `inv`, `/` and `//` are defined
(q-2)Φ₁Φ₂Φ₃⁻¹Φ₂₃

julia> -p  # one can multiply by a scalar
(-q+2)Φ₁Φ₂Φ₂₃

julia> valuation(p)
0

julia> degree(p)
25

julia> lcm(p,CycPol(q^3-1)) # lcm is fast between CycPols
(q-2)Φ₁Φ₂Φ₃Φ₂₃
```

```julia-rep1
julia> print(p)
CycPol(Pol([-2, 1]),0,(1,0),(2,0),(23,0)) # a format which can be read in Julia
```

Evaluating  a `CycPol` at some `Pol` value  gives in general a `Pol`. There are  exceptions  where  we  can  keep  the  value a `CycPol`: evaluating at `Pol()^n`  (that is `q^n`) or at  `Pol([E(n,k)],1)` (that is `qζₙᵏ`). Then `subs` gives that evaluation:

```julia-repl
julia> subs(p,Pol()^-1) # evaluate as a CycPol at q⁻¹
(2-q⁻¹)q⁻²⁴Φ₁Φ₂Φ₂₃

julia> using CyclotomicNumbers

julia> subs(p,Pol([E(2)],1)) # or at -q
(-q-2)Φ₁Φ₂Φ₄₆
```

The variable name used when printing a `CycPol` is the same as for `Pol`s.

When  showing  a  `CycPol`,  some  factors  over  extension  fields  of the cyclotomic polynomial `Φₙ` are given a special name. If `n` has a primitive root  `ξ`, `ϕ′ₙ` is the product of the  `(q-ζ)` where `ζ` runs over the odd powers  of `ξ`, and `ϕ″ₙ` is the  product for the even powers. Some further factors are recognized for small `n`. 

```julia-repl
julia> CycPol(q^6-E(4))
Φ″₈Φ⁽¹³⁾₂₄
```

The  function `show_factors` gives the  complete list of recognized factors for a given `n`:

```julia-repl
julia> CycPols.show_factors(24)
15-element Vector{Tuple{CycPol{Int64}, Pol}}:
 (Φ₂₄, q⁸-q⁴+1)
 (Φ′₂₄, q⁴+ζ₃²)
 (Φ″₂₄, q⁴+ζ₃)
 (Φ‴₂₄, q⁴-√2q³+q²-√2q+1)
 (Φ⁗₂₄, q⁴+√2q³+q²+√2q+1)
 (Φ⁽⁵⁾₂₄, q⁴-√6q³+3q²-√6q+1)
 (Φ⁽⁶⁾₂₄, q⁴+√6q³+3q²+√6q+1)
 (Φ⁽⁷⁾₂₄, q⁴+√-2q³-q²-√-2q+1)
 (Φ⁽⁸⁾₂₄, q⁴-√-2q³-q²+√-2q+1)
 (Φ⁽⁹⁾₂₄, q²+ζ₃²√-2q-ζ₃)
 (Φ⁽¹⁰⁾₂₄, q²-ζ₃²√-2q-ζ₃)
 (Φ⁽¹¹⁾₂₄, q²+ζ₃√-2q-ζ₃²)
 (Φ⁽¹²⁾₂₄, q²-ζ₃√-2q-ζ₃²)
 (Φ⁽¹³⁾₂₄, q⁴-ζ₄q²-1)
 (Φ⁽¹⁴⁾₂₄, q⁴+ζ₄q²-1)
```

Such a factor can be obtained directly as:

```julia-repl
julia> CycPol(;conductor=24,no=7)
Φ⁽⁷⁾₂₄

julia> CycPol(;conductor=24,no=7)(q)
Pol{Cyc{Int64}}: q⁴+√-2q³-q²-√-2q+1
```

This package also defines the function `cylotomic_polynomial`:

```julia-repl
julia> p=cyclotomic_polynomial(24)
Pol{Int64}: q⁸-q⁴+1

julia> CycPol(p) # same as CycPol(;conductor=24,no=0)
Φ₂₄
```

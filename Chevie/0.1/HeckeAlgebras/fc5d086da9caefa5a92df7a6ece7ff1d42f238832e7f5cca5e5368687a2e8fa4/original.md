`factorized_schur_elements(H)`

Let  `H` be  a Hecke  algebra for  the complex  reflection group `W`, whose parameters are all (Laurent) monomials in some variables `x₁,…,xₙ`, and let K  be the field of definition of `W`. Then Maria Chlouveraki has shown that the  Schur elements of `H` take the  particular form `M ∏ᵩ φ(Mᵩ)` where `φ` runs  over  a  list  of  K-cyclotomic  polynomials,  and  `M`  and `Mᵩ` are (Laurent)  monomials (in possibly some  fractional powers) of the variables `xᵢ`.  The  function  `factorized_schur_elements`  returns a data structure (see `HeckeAlgebras.FactSchur`) which shows this factorization.

```julia-repl
julia> W=complex_reflection_group(4)
G₄

julia> @Mvp x,y; H=hecke(W,[[1,x,y]])
hecke(G₄,Vector{Mvp{Int64, Int64}}[[1, x, y]])

julia> factorized_schur_elements(H)
7-element Vector{Chevie.HeckeAlgebras.FactSchur}:
 x⁻⁴y⁻⁴(xy+1)Φ₁Φ₆(x)Φ₁Φ₆(y)
 (x²y⁻¹+1)Φ₁Φ₆(x)Φ₁Φ₆(xy⁻¹)
 -x⁻⁴y⁵Φ₁Φ₆(xy⁻¹)(xy⁻²+1)Φ₁Φ₆(y)
 -x⁻¹y(xy+1)(x-1)Φ₆(xy⁻¹)(y-1)
 -x⁻⁴y(x²y⁻¹+1)(x-1)(xy⁻¹-1)Φ₆(y)
 x⁻¹y⁻¹Φ₆(x)(xy⁻¹-1)(xy⁻²+1)(y-1)
 x⁻²y(x²y⁻¹+1)(xy+1)(xy⁻²+1)
```

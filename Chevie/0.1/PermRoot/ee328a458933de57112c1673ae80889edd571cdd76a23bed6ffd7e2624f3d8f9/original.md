`catalan(W::ComplexReflectionGroup)`

returns the Catalan Number of the irreducible complex reflection group `W`. For well-generated groups, this number is equal to the number of simples in the  dual Braid  monoid. For  other groups  it was  defined by  [Gordon and Griffeth2012](biblio.htm#gg12).  For Weyl groups, it also counts the number of antichains of roots.

```julia-repl
julia> catalan(coxgroup(:A,7))
1430
```

`catalan(W,i)`

returns   the  `i`-th  Fuss-Catalan  Number   of  the  irreducible  complex reflection  group `W`. For  well-generated groups, this  number is equal to the  number of chains  `s₁,…,sᵢ` of simples  in the dual  monoid where `sⱼ` divides  `sⱼ₊₁`. For these groups, it is also equal to `∏ⱼ(ih+dⱼ)/dⱼ` where the  product runs over the reflection degrees  of `W`, and where `h` is the Coxeter  number of `W`. For non-well generated groups, the definition is in [Gordon and Griffeth2012](biblio.htm#gg12).

```julia-repl
julia> catalan(complex_reflection_group(7),2)
16
```

`catalan(W;q=1)`, resp. `catalan(W,i;q=1)`

for  `q`  a  variable  (like  `Pol()`  or an `Mvp`) returns the `q`-Catalan number  (resp.  the  `i`-th  `q`-Fuss  Catalan  number)  of  `W`. Again the definitions in general are in [Gordon and Griffeth2012](biblio.htm#gg12).

```julia-repl
julia> catalan(complex_reflection_group(7),2;q=Pol())
Pol{Int64}: q⁷²+2q⁶⁰+3q⁴⁸+4q³⁶+3q²⁴+2q¹²+1
```

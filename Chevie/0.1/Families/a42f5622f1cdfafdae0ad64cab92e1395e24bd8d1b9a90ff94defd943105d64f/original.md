`galois(f::Family,p::Int)`

`x->galois(x,p)`  is  applied  to  the  Fourier  matrix  and eigenvalues of Frobenius of the family.

```julia-repl
julia> f=UnipotentCharacters(complex_reflection_group(3,1,1)).families[2]
Family(0011,[4, 3, 2],cospecial=2)
imprimitive family
┌─────┬──────────────────────────────┐
│label│eigen      1        2        3│
├─────┼──────────────────────────────┤
│1    │  ζ₃²  √-3/3    √-3/3   -√-3/3│
│2    │    1  √-3/3 ζ₃²√-3/3 -ζ₃√-3/3│
│3    │    1 -√-3/3 -ζ₃√-3/3 ζ₃²√-3/3│
└─────┴──────────────────────────────┘

julia> galois(f,-1)
Family(conj(0011),[4, 3, 2],cospecial=2)
conj(imprimitive family)
┌─────┬──────────────────────────────┐
│label│eigen      1        2        3│
├─────┼──────────────────────────────┤
│1    │   ζ₃ -√-3/3   -√-3/3    √-3/3│
│2    │    1 -√-3/3 -ζ₃√-3/3 ζ₃²√-3/3│
│3    │    1  √-3/3 ζ₃²√-3/3 -ζ₃√-3/3│
└─────┴──────────────────────────────┘
```

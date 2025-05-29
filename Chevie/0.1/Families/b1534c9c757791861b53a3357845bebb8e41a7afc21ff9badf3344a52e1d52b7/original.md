`Family(f [, charNumbers [, opt]])`

This function creates a new family in two possible ways.

In  the first case `f` is a string which denotes a family known to  Chevie. Examples are "S3",   "S4",   "S5"   which denote the family obtained as the Drinfeld  double of the symmetric group  on 3,4,5 elements, or "C2"   which denotes the Drinfeld double of the cyclic group of order 2.

In the second case `f` is already a `struct Family`.

The other (optional) arguments add information to the family defined by the first argument. If given, the second argument becomes `f.charNumbers`. If given,  the third argument  `opt` is a  `Dict` whose keys  are added to the resulting family.

If `opt` has a key `signs`, this should be a list of '1' and '-1', and then the  Fourier matrix  is conjugated  by the  diagonal matrix of those signs. This  is used  in Spetses  to adjust  the matrix  to the choice of signs of unipotent degrees.

```julia-repl
julia> Family("C2")
Family(C₂)
Drinfeld double D(ℤ/2)
┌──────┬────────────────────────────┐
│label │eigen                       │
├──────┼────────────────────────────┤
│(1,1) │    1 1//2  1//2  1//2  1//2│
│(g₂,1)│    1 1//2  1//2 -1//2 -1//2│
│(1,ε) │    1 1//2 -1//2  1//2 -1//2│
│(g₂,ε)│   -1 1//2 -1//2 -1//2  1//2│
└──────┴────────────────────────────┘

julia> Family("C2",4:7;signs=[1,-1,1,-1])
Family(C₂,4:7,signs=[1, -1, 1, -1])
Drinfeld double D(ℤ/2)
┌──────┬──────────────────────────────────┐
│label │eigen signs                       │
├──────┼──────────────────────────────────┤
│(1,1) │    1     1  1//2 -1//2 1//2 -1//2│
│(g₂,1)│    1    -1 -1//2  1//2 1//2 -1//2│
│(1,ε) │    1     1  1//2  1//2 1//2  1//2│
│(g₂,ε)│   -1    -1 -1//2 -1//2 1//2  1//2│
└──────┴──────────────────────────────────┘
```

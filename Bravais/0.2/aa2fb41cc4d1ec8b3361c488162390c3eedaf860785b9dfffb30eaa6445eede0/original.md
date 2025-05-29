```
centering(sgnum::Integer, D::Integer=3)  -->  Char
```

Return the conventional centering type `cntr` of the space group with number `sgnum` and dimension `D`.

The centering type is equal to the first letter of the Hermann-Mauguin notation's label, i.e., `centering(sgnum, D) == first(Crystalline.iuc(sgnum, D))`. Equivalently, the centering type is the second and last letter of the Bravais type ([`bravaistype`](@ref)), i.e., `centering(sgnum, D) == bravaistype(sgnum, D)`.

Possible values of `cntr`, depending on dimensionality `D`, are (see ITA Sec. 9.1.4):

  * `D = 1`:

      * `cntr = 'p'`: no centering (primitive)
  * `D = 2`:

      * `cntr = 'p'`: no centring (primitive)
      * `cntr = 'c'`: face centered
  * `D = 3`: 

      * `cntr = 'P'`: no centring (primitive)
      * `cntr = 'I'`: body centred (innenzentriert)
      * `cntr = 'F'`: all-face centred
      * `cntr = 'A'` or `'C'`: one-face centred, (b,c) or (a,b)
      * `cntr = 'R'`: hexagonal cell rhombohedrally centred

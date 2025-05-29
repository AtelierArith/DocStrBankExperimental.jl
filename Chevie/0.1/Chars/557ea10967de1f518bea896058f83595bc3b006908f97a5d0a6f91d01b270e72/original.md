`charinfo(W)`

returns   information  about  the  irreducible  characters  of  the  finite reflection group or Spets `W`. The result is an object with various entries describing  properties of  the irreducible  characters of  `W`. This object prints  at the  Repl or  in Pluto  or Jupyter  as a table synthesizing most information.

A  field not in the table is  `.charparams`: it contains parameters for the irreducible  characters.  A  parameter  is  a  list  with one item for each irreducible  component of `W` (as given  by `refltype`). For an irreducible `W` see the helpstring for `Chars` for what are the parameters.

```julia-repl
julia> charinfo(coxgroup(:G,2)).charparams
6-element Vector{Vector{Vector{Int64}}}:
 [[1, 0]]
 [[1, 6]]
 [[1, 3, 1]]
 [[1, 3, 2]]
 [[2, 1]]
 [[2, 2]]
```

```julia-repl
julia> charinfo(coxgroup(:G,2))
┌──┬──────────────────────────────────────────────────────────┐
│n0│ name ext b B a A spaltenstein lusztig              symbol│
├──┼──────────────────────────────────────────────────────────┤
│1 │ φ₁‚₀  Id 0 0 0 0            1       1       (0,0,0,0,0,2)│
│2 │ φ₁‚₆ det 6 6 6 6            ε       ε (01,01,01,01,01,12)│
│3 │φ′₁‚₃     3 3 1 5           εₗ      ε′            (0,0,1+)│
│4 │φ″₁‚₃     3 3 1 5          ε_c      ε″            (0,0,1-)│
│5 │ φ₂‚₁  Λ¹ 1 5 1 5           θ′      θ′       (0,0,0,0,1,1)│
│6 │ φ₂‚₂     2 4 1 5           θ″      θ″       (0,0,0,1,0,1)│
└──┴──────────────────────────────────────────────────────────┘
```

In  the table printed  at the Repl,  the columns reflect  various fields of `charinfo`.  The  column  `name`  reflects  the  field `.charnames`, a name computed  from `.charparams`. This  is the same  as `charnames(io,W)` where here `io` being the Repl has the property `:limit` true.

The   column   `ext`   shows   the   exterior   powers  of  the  reflection representation.  It corresponds  to the  field `.extrefl`  which is present only  if `W`  is irreducible.  Otherwise, only  two items  are shown in the column:  `Id` corresponds to the field  `.positionId` and shows the trivial character.  `det`  corresponds  to  the  field `.positionDet` and shows the determinant  character (for Coxeter groups the sign character). When `W` is irreducible,  the characters marked  `Λⁱ` are the  `i`-th exterior power of the  reflection  representation.  They  are  irreducible  by  a  theorem of Steinberg.

The  column  `b`  shows  the  field  `.b`  listing  for  each character the valuation  of the fake degree, and the column `B` shows the field `.B`, the degree of the fake degree.

The  columns `a` and  `A` only appear  for Spetsial groups. They correspond then  to the fields  `.a` and `.A`,  and contain respectively the valuation and the degree of the generic degree of the character (in the one-parameter Hecke algebra `hecke(W,Pol())` for `W`).

For  irreducible  groups,  the  table  shows  sometimes additional columns, corresponding to a field of the same name.

for  `F₄`, the column `kondo` gives the labeling of the characters given by Kondo, also used in [Lusztig1985, (4.10)](biblio.htm#Lus85).

for  `E₆, E₇, E₈` the  column `frame` gives the  labeling of the characters given   by  Frame,   also  used   in  [Lusztig1985,   (4.11),  (4.12),  and (4.13)](biblio.htm#Lus85).

for  `G₂` the  column `spaltenstein`  gives the  labeling of the characters given by Spaltenstein.

for `G(de,e,2)` even `e` and `d>1`, the column `malle` gives the parameters for the characters used in [Malle1996](biblio.htm#Mal96).

If  `W`  is  irreducible  spetsial  and  imprimitive,  the  column 'symbol`(corresponding  to the field`.charSymbols`) shows the  symbol attached to the corresponding unipotent caracter.

If  `W  isa  Spets`,  the  column  `restr.`  (corresponding  to  the  field `.charRestrictions`)  gives the  number of  the corresponding  character of `Group(W)`.

Finally,  the  field  `.hgal`  contains  the  permutation of the characters resulting  from a Galois  action on the  characters of `H=hecke(W,Pol()^e)` where  `e` is the order of  the center of `W`. `H`  splits by taking `v` an `e`-th root of `Pol()`, and `.hgal` records the permutation effected by the Galois action `v->E(e)*v` (`charinfo` does not have the key `:hgal` if this permutation   is  trivial).  `.hgal*conj`,  where  `conj`  is  the  complex conjugaison, is the Opdam involution.

```julia-repl
julia> charinfo(complex_reflection_group(24))
┌──┬─────────────────────┐
│n0│ name ext  b  B  a  A│
├──┼─────────────────────┤
│1 │ φ₁‚₀  Id  0  0  0  0│
│2 │φ₁‚₂₁ det 21 21 21 21│
│3 │ φ₃‚₈      8 18  8 20│
│4 │ φ₃‚₁  Λ¹  1 11  1 13│
│5 │φ₃‚₁₀  Λ² 10 20  8 20│
│6 │ φ₃‚₃      3 13  1 13│
│7 │ φ₆‚₂      2 12  1 13│
│8 │ φ₆‚₉      9 19  8 20│
│9 │ φ₇‚₆      6 18  6 18│
│10│ φ₇‚₃      3 15  3 15│
│11│ φ₈‚₄      4 16  4 17│
│12│ φ₈‚₅      5 17  4 17│
└──┴─────────────────────┘
hgal=(11,12)
```

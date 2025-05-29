`UnipotentCharacters(W)`

`W`  should be a Coxeter group, a  Coxeter Coset or a Spetses. The function gives  back a record containing  information about the unipotent characters of the associated algebraic group (or Spetses). This contains the following fields:

`.harishChandra`:  information  about  Harish-Chandra  series  of  unipotent characters.  This is itself a list of records, one for each pair `(𝐋,λ)` of a  Levi  of  an  `F`-stable  parabolic  subgroup  and  a cuspidal unipotent character of $𝐋^F$. These records themselves have the following fields:

`:levi`: a list 'l' such that `𝐋` corresponds to 'reflection_subgroup(W,l)'.

`:cuspidalName`: the name of the unipotent cuspidal character `lambda`.

`:eigenvalue`: the eigenvalue of Frobenius for `λ`.

`:relativeType`: the reflection type of $W_𝐆 (𝐋)$;

`:parameterExponents`:  the $𝐆 ^F$-endomorphism  algebra of $R_𝐋^𝐆 (λ)$ is  a  Hecke  algebra  for  $W_𝐆  (𝐋)$  with  some parameters of the form $q^{a_s}$. This holds the list of exponents $a_s$.

`:charNumbers`:  the  indices  of  the  unipotent  characters indexed by the irreducible characters of $W_𝐆 (𝐋)$.

`.almostHarishChandra`:   information   about   Harish-Chandra   series  of unipotent  character sheaves.  This is  identical to  ̀harishChandra` for a split  reductive group,  and reflects  the situation  for the corresponding split group for a nonsplit group.

`.families`:  information  about  Lusztig  families of unipotent characters. This  is itself a list  of records, one for  each family. These records are described in the section about families below.

the following information is computed on demand from `uc=UnipotentCharacters(W)`:

`spets(uc)`: the reductive group `W`.

```julia-repl
julia> W=coxgroup(:Bsym,2)
Bsym₂

julia> WF=spets(W,Perm(1,2))
²Bsym₂

julia> uc=UnipotentCharacters(WF)
UnipotentCharacters(²Bsym₂)
┌────────┬─────────────────────────────────────────────────────┐
│γ       │n₀ almostch    Deg(γ)   Feg        Symbol Fr(γ) label│
├────────┼─────────────────────────────────────────────────────┤
│2       │ 1       2.         1     1     (02,,0,0)     1      │
│11      │ 2      .11        q⁴    q⁴ (012,1,01,01)     1      │
│²B₂[1,3]│ 3      1.1 √2qΦ₁Φ₂/2 qΦ₁Φ₂     (01,,1,0)   ζ₈³     1│
│²B₂[1,5]│ 4       B₂ √2qΦ₁Φ₂/2     0     (01,,0,1)   ζ₈⁵     2│
└────────┴─────────────────────────────────────────────────────┘

julia> uc.families
3-element Vector{Family}:
 Family(C₁,[1])
 Family(C₁,[2])
 Family(?4,[3, 4])

julia> uc.families[3]
Family(?4,[3, 4])
┌─────┬────────────────┐
│label│eigen    1     2│
├─────┼────────────────┤
│1    │  ζ₈³ √2/2 -√2/2│
│2    │  -ζ₈ √2/2  √2/2│
└─────┴────────────────┘
```

`charnames(uc)`:  the list of names of the unipotent characters.  Using    appropriate keywords, one can control the display in various ways.

```julia-repl
julia> uc=UnipotentCharacters(coxgroup(:G,2));

julia> charnames(uc;limit=true)
10-element Vector{String}:
 "φ₁‚₀"
 "φ₁‚₆"
 "φ′₁‚₃"
 "φ″₁‚₃"
 "φ₂‚₁"
 "φ₂‚₂"
 "G₂[-1]"
 "G₂[1]"
 "G₂[ζ₃]"
 "G₂[ζ₃²]"

julia> charnames(uc;TeX=true)
10-element Vector{String}:
 "\phi_{1,0}"
 "\phi_{1,6}"
 "\phi_{1,3}'"
 "\phi_{1,3}''"
 "\phi_{2,1}"
 "\phi_{2,2}"
 "G_2[-1]"
 "G_2[1]"
 "G_2[\zeta_3]"
 "G_2[\zeta_3^2]"
```

One  can control  the display  of unipotent  characters in  various ways by `IOContext` properties. In the display, the row labels are the names of the unipotent characters. The possible columns are numbered as follows:

1. The index of the character in the list of unipotent characters.
2. The degree of the unipotent character.
3. The degree of the corresponding almost character.
4. for imprimitive groups, the symbol attached to the unipotent character.
5. The eigenvalue of Frobenius attached to the unipotent character.
6. The parameter the character has in its Lusztig family.

Which  columns  are  displayed  can  be  controlled by the property `:cols` (default [2,3,5,6] and 4 when applicable).

In  addition if  ':byfamily=true', the  characters are  displayed family by family  instead  of  in  index  order.  Finally,  the properties `rows` and `columnrepartition`  of  `format`  can  be  set,  giving more tuning of the table.

```julia-repl
julia> W=coxgroup(:B,2)
B₂

julia> uc=UnipotentCharacters(W)
UnipotentCharacters(B₂)
┌───┬──────────────────────────────────┐
│γ  │n₀ Deg(γ) Feg   Symbol Fr(γ) label│
├───┼──────────────────────────────────┤
│11.│ 1  qΦ₄/2  q²   (12,0)     1   +,-│
│1.1│ 2 qΦ₂²/2 qΦ₄   (02,1)     1   +,+│
│.11│ 3     q⁴  q⁴ (012,12)     1      │
│2. │ 4      1   1     (2,)     1      │
│.2 │ 5  qΦ₄/2  q²   (01,2)     1   -,+│
│B₂ │ 6 qΦ₁²/2   0   (012,)    -1   -,-│
└───┴──────────────────────────────────┘
```

```julia-rep1
julia> xdisplay(uc;byfamily=true)
┌────┬──────────────────────────────────┐
│γ   │n₀ Deg(γ) Feg   Symbol Fr(γ) label│
├────┼──────────────────────────────────┤
│11. │ 1  qΦ₄/2  q²   (12,0)     1   +,-│
│1.1ˢ│ 2 qΦ₂²/2 qΦ₄   (02,1)     1   +,+│
│.2  │ 5  qΦ₄/2  q²   (01,2)     1   -,+│
│B₂  │ 6 qΦ₁²/2   0   (012,)    -1   -,-│
├────┼──────────────────────────────────┤
│2.  │ 4      1   1     (2,)     1      │
├────┼──────────────────────────────────┤
│.11 │ 3     q⁴  q⁴ (012,12)     1      │
└────┴──────────────────────────────────┘

julia> xdisplay(uc;cols=[1,4])
UnipotentCharacters(B₂)
┌───┬───────────┐
│γ  │n₀   Symbol│
├───┼───────────┤
│11.│ 1   (12,0)│
│1.1│ 2   (02,1)│
│.11│ 3 (012,12)│
│2. │ 4     (2,)│
│.2 │ 5   (01,2)│
│B₂ │ 6   (012,)│
└───┴───────────┘
```

`ICCTable(uc,seriesNo=1;q=Pol())`

This function gives the table of decompositions of the functions $X_ι$ in terms  of the functions $Y_ι$. Here `ι` is a `𝐆`-equivariant local system on  the  class  `C`  of  a  unipotent  element  `u`. Such a local system is parametrised  by the pair  `(u,ϕ)` of `u`  and a character  of the group of components   `A(u)`   of   $C_𝐆   (u)$.   The  function  $Y_ι$  is  the characteristic   function  of  this   local  system  and   $X_ι$  is  the characteristic   function  of  the  corresponding  intersection  cohomology complex  on `C̄`. The  Springer correspondence says  that the local systems can  also be  indexed by  characters of  a relative  Weyl group.  Since the coefficient of `Xᵪ` on `Yᵩ` is `0` if `χ` and `φ` are not characters of the same  relative Weyl group (are not in  the same Springer series), the table is  for one  Springer series,  specified by  the argument  'seriesNo' (this defaults  to 'seriesNo=1' which is the principal series). The decomposition multiplicities  are graded,  and are  given as  polynomials in one variable (specified by the argument `q`; if not given `Pol()` is assumed).

```julia-repl
julia> uc=UnipotentClasses(coxgroup(:A,3));t=ICCTable(uc)
Coefficients of Xᵪ on Yᵩ for series L=A₃₍₎=Φ₁³ W_G(L)=A₃
┌─────┬────────────────┐
│X\Y  │4 31 22 211 1111│
├─────┼────────────────┤
│X4   │1  1  1   1    1│
│X31  │.  1  1  Φ₂   Φ₃│
│X22  │.  .  1   1   Φ₄│
│X211 │.  .  .   1   Φ₃│
│X1111│.  .  .   .    1│
└─────┴────────────────┘
```

In  the  above  the  multiplicities  are  given  as  products of cyclotomic polynomials  to display them  more compactly. However  the format of such a table can be controlled more precisely.

For  instance,  one  can  ask  to  not  display  the entries as products of cyclotomic polynomials and not display the zeroes as '.'

```julia-rep1
julia> xdisplay(t;cycpol=false,dotzero=false)
Coefficients of Xᵪ on Yᵩ for A3
┌─────┬──────────────────┐
│X\Y  │4 31 22 211   1111│
├─────┼──────────────────┤
│X4   │1  1  1   1      1│
│X31  │0  1  1 q+1 q²+q+1│
│X22  │0  0  1   1   q²+1│
│X211 │0  0  0   1 q²+q+1│
│X1111│0  0  0   0      1│
└─────┴──────────────────┘
```

Since  `show`  uses  the  function  `showtable`,  all  the  options of this function  are  also  available.  We  can  use  this to restrict the entries displayed  to a  given sublist  of the  rows and  columns (here the indices correspond  to the number  in Chevie of  the corresponding character of the relative Weyl group of the given Springer series):

```julia-rep1
julia> uc=UnipotentClasses(coxgroup(:F,4));
julia> t=ICCTable(uc);
julia> sh=[13,24,22,18,14,9,11,19];
julia> xdisplay(t,rows=sh,cols=sh)
Coefficients of Xᵪ on Yᵩ for series L=F₄₍₎=Φ₁⁴ W_G(L)=F₄
┌───────┬────────────────────────────────────────────┐
│X\Y    │A₁+Ã₁ A₂ Ã₂ A₂+Ã₁ Ã₂+A₁ B₂⁽¹¹⁾ B₂ C₃(a₁)⁽¹¹⁾│
├───────┼────────────────────────────────────────────┤
│Xφ₉‚₁₀ │    1  .  .     .     .      .  .          .│
│Xφ″₈‚₉ │    1  1  .     .     .      .  .          .│
│Xφ′₈‚₉ │    1  .  1     .     .      .  .          .│
│Xφ″₄‚₇ │    1  1  .     1     .      .  .          .│
│Xφ′₆‚₆ │   Φ₄  1  1     1     1      .  .          .│
│Xφ₄‚₈  │   q²  .  .     .     .      1  .          .│
│Xφ″₉‚₆ │   Φ₄ Φ₄  .     1     .      .  1          .│
│Xφ′₄‚₇ │   q²  . Φ₄     .     1      .  .          1│
└───────┴────────────────────────────────────────────┘
```

The  `ìo` option `rowlocsys=true`  will display local  systems also for the row labels.

The   function  'ICCTable'  returns  an   object  with  various  pieces  of information which can help further computations.

`.scalar`:  this contains the table of  multiplicities `Pᵪᵩ` of the `Xᵪ` on the  `Yᵩ`.  One  should  pay  attention  that  by default, the table is not displayed  in the same order as the  stored |.scalar|, which is in order in Chevie  of  the  characters  in  the  relative  Weyl  group;  the  table is transposed,  then lines  and rows  are sorted  by `dimBu,class  no,index of character in A(u)` while displayed.

`.group`: The group `W`.

`.relgroup`: The relative Weyl group for the Springer series.

`.series`: The index of the Springer series given for `W`.

`.dimBu`: The list of $dimℬᵤ$ for each local system `(u,φ)` in the series.

`:L`:  The matrix of (unnormalised) scalar products of the functions $Yᵩ$ with  themselves,  that  is  the  $(φ,χ)$  entry  is $∑_{g∈𝐆(𝔽_q)} Yᵩ(g) Yᵪ(g)$. This is thus a symmetric, block-diagonal matrix where the diagonal blocks  correspond to geometric unipotent conjugacy classes. This matrix is obtained as a by-product of Lusztig's algorithm to compute $Pᵩᵪ$.

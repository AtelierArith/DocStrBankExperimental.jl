`XSP(ρ,s,n,even=false)`

returns  the  union  of  the [Lusztig-Spaltenstein 1985](biblio.htm#LuSp85) $X̃^{ρ-s,s}_{n,d}$  for  all  `d`  even  when  `even=true`,  all  `d` odd otherwise;  these symbols parametrize local  systems on unipotent conjugacy classes  for classical groups. In [Lusztig2004](biblio.htm#Lus04), 13.2 the notation  is ${}^ρ X^s_{n,d}$.  The result is  a list of  lists, each one corresponding  to a similarity class (which correspond to a given conjugacy class for the support). If `s==0`, only positive defects are considered.

  * `XSP(2,1,n)` gives L-S symbols for Sp₂ₙ
  * `XSP(4,2,n)` gives L-S symbols for Sp₂ₙ in char.2
  * `XSP(2,0,n)` gives L-S symbols for SO₂ₙ₊₁ [defect odd]
  * `XSP(2,0,n,true)` gives L-S symbols for SO₂ₙ [defect even]
  * `XSP(4,0,n,true)` gives L-S symbols for SO₂ₙ in char 2

each item is a `NamedTuple` giving some information on the local system. It has fields

  * `symbol` the Lusztig-Spaltenstein symbol
  * `dimBu` for the support `u` of the local system
  * `Au` describes the character  of `A(u)` for the  local system as a list: `true`->sgn, `false`->Id
  * `sp`  parameter (double partition) of the generalized Springer  correspondent (a character of the relative Weyl group)

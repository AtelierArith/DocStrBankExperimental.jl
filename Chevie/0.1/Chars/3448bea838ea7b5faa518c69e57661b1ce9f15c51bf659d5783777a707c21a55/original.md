Characters and conjugacy classes of complex reflection groups.

The  `CharTable` of a finite complex reflection group `W` is computed using the  decomposition of `W` in irreducible  groups (see `refltype`). For each irreducible  group the character  table is either  computed using recursive formulas  for the infinite series,  or read into the  system from a library file  for the  exceptional types.  Thus, character  tables can  be obtained quickly  even for very large groups  (e.g., E₈). Similar remarks apply for conjugacy classes.

The  conjugacy  classes  and  irreducible  characters of irreducible finite complex reflection groups have canonical labelings by certain combinatorial objects;  these labelings are used in the  tables we give. For the classes, these  are partitions or partition tuples  for the infinite series, or, for exceptional  Coxeter  groups,  Carter's  admissible  diagrams [Carter1972](biblio.htm#Car72); for other  primitive  complex  reflection  groups  we  just  use  words  in the generators  to specify  the classes.  For the  characters, these  are again partitions  or partition tuples for the infinite series, and for the others they  are pairs  of two  integers `(d,e)`  where `d`  is the  degree of the character  and  `e`  is  the  smallest  symmetric  power  of the reflection representation  containing  the  given  character  as  a  constituent  (the `b`-invariant of the character). This information is given by the functions `classinfo`  and  `charinfo`.  When  you  display  the character table, the canonical labelings for classes and characters are displayed.

A  typical example  is `coxgroup(:A,n)`,  the symmetric  group `𝔖ₙ₊₁` where classes  and characters are  parameterized by partitions  of `n+1` (this is also the case for `coxsym(n+1)`).

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> CharTable(W)
CharTable(A₃)
┌────┬─────────────────┐
│    │1111 211 22 31  4│
├────┼─────────────────┤
│1111│   1  -1  1  1 -1│
│211 │   3  -1 -1  .  1│
│22  │   2   .  2 -1  .│
│31  │   3   1 -1  . -1│
│4   │   1   1  1  1  1│
└────┴─────────────────┘

julia> W=coxgroup(:G,2)
G₂

julia> ct=CharTable(W)
CharTable(G₂)
┌─────┬────────────────────┐
│     │A₀ Ã₁ A₁ G₂ A₂ A₁+Ã₁│
├─────┼────────────────────┤
│φ₁‚₀ │ 1  1  1  1  1     1│
│φ₁‚₆ │ 1 -1 -1  1  1     1│
│φ′₁‚₃│ 1  1 -1 -1  1    -1│
│φ″₁‚₃│ 1 -1  1 -1  1    -1│
│φ₂‚₁ │ 2  .  .  1 -1    -2│
│φ₂‚₂ │ 2  .  . -1 -1     2│
└─────┴────────────────────┘

julia> ct.charnames
6-element Vector{String}:
 "\phi_{1,0}"
 "\phi_{1,6}"
 "\phi_{1,3}'"
 "\phi_{1,3}''"
 "\phi_{2,1}"
 "\phi_{2,2}"

julia> ct.classnames
6-element Vector{String}:
 "A_0"
 "\tilde A_1"
 "A_1"
 "G_2"
 "A_2"
 "A_1+\tilde A_1"
```

Reflection  groups  have  fake  degrees  (see [`fakedegrees`](@ref)), whose valuation and degree give two integers `b,B` for each irreducible character of  `W`. For  spetsial groups  (which include  finite Coxeter  groups), the valuation  and degree of the generic degrees  of the Hecke algebra give two more integers `a,A` (for Coxeter groups see [Carter1985, Ch.11](biblio.htm#Car85) for more details). These integers are also used in the  operations of  truncated induction,  see [`j_induction_table`](@ref) and [`J_induction_table`](@ref).

Iwahori-Hecke  algebras and  cyclotomic Hecke  algebras also have character tables, see the corresponding chapters.

We  now describe for each type our conventions for labeling the classes and characters.

Type  `Aₙ`  (`n≥0`).  In  this  case  we  have  `W ≅ 𝔖ₙ₊₁`. The classes and characters  are labelled by partitions of  `n+1`. The partition labelling a class  is the cycle type of the  elements in that class; the representative in  '.classtext' is  the concatenation  of the  words corresponding to each part,  where the word for a part  `i` is  the  product of `i-1` consecutive generators  (starting  one  higher  than  the  last  generator used for the previous  parts). The partition labelling a character describes the type of the  Young  subgroup  such  that  the  trivial  character induced from this subgroup  contains that character with multiplicity `1` and such that every other character occurring in this induced character has a higher `a`-value. Thus,  the sign  character is  labelled by  the partition  `(1ⁿ⁺¹)` and the trivial character by the partition `(n+1)`. The character of the reflection representation of `W` is labelled by `(n,1)`.

Type  `Bₙ`  (`n≥2`).  In  this  case  `W=W(Bₙ)` is isomorphic to the wreath product  of the cyclic  group of order  `2` with the  symmetric group `𝔖ₙ`. Hence  the classes and characters are  parameterized by pairs of partitions such  that the total sum of their  parts equals `n`. The pair corresponding to  a class describes the signed cycle type for the elements in that class, as in [Carter1972](biblio.htm#Car72). We use the convention that if `(λ,μ)` is such a pair then `λ` corresponds to the positive and `μ` to the negative cycles.  Thus, `(1ⁿ,-)` and  `(-,1ⁿ)` label respectively  the trivial class and  the  class  of  the  longest  element.

The  pair  corresponding  to  an  irreducible  character  is determined via Clifford  theory, as  follows. We  have a  semidirect product decomposition `W(Bₙ)=N  ⋊  𝔖ₙ`  where  `N`  is  the standard `n`-dimensional `𝔽₂ⁿ`-vector space.  For `a,b ≥ 0` such that  `n=a+b` let $η_{a,b}$ be the irreducible character  of `N`  which takes  value `1`  on the  first `a` standard basis vectors  and value `-1` on the last `b` standard basis vectors of `N`. Then the  inertia subgroup of $η_{a,b}$ has the form $T_{a,b}=N.(𝔖_a × 𝔖_b)$ and  we  can  extend  $η_{a,b}$  trivially  to  an  irreducible character $η̃_{a,b}$  of $T_{a,b}$. Let `α` and `β` be partitions of `a` and `b`, respectively.  We take the tensor  product of the corresponding irreducible characters  of `𝔖_a` and `𝔖_b` and  regard this as an irreducible character of  $T_{a,b}$. Multiplying this character  with $η̃_{a,b}$ and inducing to  `W(Bₙ)` yields  an irreducible  character $χ=  χ_{(α,β)}$ of `W(Bₙ)`. This defines the correspondence between irreducible characters and pairs of partitions as above.

For example, the pair `((n),-)` labels the trivial character and `(-,(1ⁿ))` labels  the  sign  character.  The  character  of  the  natural  reflection representation is labeled by `((n-1),(1))`.

Type  `Dₙ` (`n≥4`). In this case `W=W(Dₙ)` can be embedded as a subgroup of index  `2` into the Coxeter  group `W(Bₙ)`. The intersection  of a class of `W(Bₙ)` with `W(Dₙ)` is either empty or a single class in `W(Dₙ)` or splits up  into two classes in  `W(Dₙ)`. This also leads  to a parameterization of the  classes of `W(Dₙ)` by pairs of  partitions `(λ,μ)` as before but where the  number of parts of `μ` is even and where there are two classes of this type  if `μ` is empty and all parts of  `λ` are even. In the latter case we denote  the two classes in `W(Dₙ)` by `(λ,+)` and `(λ,-)`, where we use the convention  that  the  class  labeled  by `(λ,+)` contains a representative which  can be written  as a word  in `{s₁,s₃,…,sₙ}` and  `(λ,-)` contains a representative which can be written as a word in `{s₂,s₃, …,sₙ}`.

By  Clifford theory the restriction of  an irreducible character of `W(Bₙ)` to  `W(Dₙ)`  is  either  irreducible  or  splits  up  into  two irreducible components.  Let `(α,β)` be  a pair of  partitions with total  sum of parts equal to `n`. If `α!=β` then the restrictions of the irreducible characters of  `W(Bₙ)` labeled  by `(α,β)`  and `(β,α)`  are irreducible and equal. If `α=β`  then the restriction of the character labeled by `(α,α)` splits into two  irreducible components  which we  denote by  `(α,+)` and `(α,-)`. Note that  this can only happen if `n` is  even. In order to fix the notation we use  a  result  of  [Stembridge1989](biblio.htm#Ste89)  which describes the value  of the  difference of  these two  characters on  a class of the form `(λ,+)`  in terms of the character values of the symmetric group `𝔖_{n/2}`. Recall  that it is implicit  in the notation `(λ,+)`  that all parts of `λ` are even. Let `λ'` be the partition of `n/2` obtained by dividing each part by  `2`. Then the value of `χ_{(α,-)}-χ_{(α,+)}` on an element in the class `(λ,+)` is given by `2^{k(λ)}` times the value of the irreducible character of  `𝔖_{n/2}` labeled by `α` on the class of cycle type `λ'`. (Here, `k(λ)` denotes the number of non-zero parts of `λ`.)

The  labels for the trivial, the  sign and the natural reflection character are the same as for `W(Bₙ)`, since these characters are restrictions of the corresponding characters of `W(Bₙ)`.

The groups `G(d,1,n)`. They  are isomorphic to the wreath product of the cyclic group of order `d` with  the  symmetric  group  `𝔖ₙ`.  Hence  the  classes  and characters are parameterized  by `d`-tuples of partitions such that the total sum of their parts  equals `n`. The words chosen  as representatives of the classes are, when `d>2`, computed in a slightly different way than for `Bₙ`, in order to agree  with the words on which Ram  and Halverson compute the characters of the  Hecke algebra. First the parts of the `d` partitions are merged in one big  partition and sorted in  increasing order. Then, to  a part `i` coming from  the `j`-th partition is  associated the word `(l+1…1… l+1)ʲ⁻¹l+2…l+i` where `l` is the highest generator used to express the previous part.

The  `d`-tuple corresponding to an  irreducible character is determined via Clifford  theory in  a similar  way than  for the  `Bₙ` case.  The identity character  has the first  partition with one  part equal `n`  and the other ones  empty. The character of the  reflection representations has the first two  partitions with one part  equal respectively to `n-1`  and to `1`, and the other partitions empty.

The groups `G(de,e,n)`. They  are normal  subgroups of  index `e`  in `G(de,1,n)`.  The quotient is cyclic,  generated by the image `g`  of the first generator of `G(de,1,n)`. The  classes are parameterized as the  classes of `G(de,e,n)` with an extra information for a component of a class which splits.

According  to  [Hugues1985](biblio.htm#Hu85),  a  class  `C` of `G(de,1,n)` parameterized  by a `de`-partition $(S₀,…,S_{de-1})$ is in `G(de,e,n)` if `e`  divides $∑ᵢ i ∑_{p∈ Sᵢ}p$. It  splits in `d` classes for the largest `d`  dividing `e` and all parts of all  `Sᵢ` and such that `Sᵢ` is empty if `d`  does not divide `i`. If `w` is in `C` then 'gⁱ w g⁻ⁱ' for 'i in 0:d-1' are  representatives of the classes of `G(de,e,n)` which meet `C`. They are described by appending the integer `i` to the label for `C`.

The  characters are described by Clifford theory. We make `g` act on labels for  characters of `G(de,1,n)`  . The action  of `g` permutes circularly by `d`  the partitions in the `de`-tuple.  A character has same restriction to `G(de,e,n)`  as its transform by `g`.  The number of irreducible components of its restriction is equal to the order `k` of its stabilizer under powers of  `g`.  We  encode  a  character  of  `G(de,e,n)`  by first, choosing the smallest  for lexicographical order label  of a character whose restriction contains  it; then this label is periodic with a motive repeated `k` times; we  represent the  character by  one of  these motives,  to which we append `E(k)ⁱ` for 'i in 0:k-1' to describe which component of the restriction we choose.

Types `G₂` and `F₄`. The matrices of character values and the orderings and labelings  of  the  irreducible  characters  are  exactly  the  same  as in [Carter1985,  p.412/413](biblio.htm#Car85):  in  type  `G₂`  the  character `φ₁,₃'`  takes the value -1 on the reflection associated to the long simple root;  in type `F₄`, the characters `φ₁,₁₂'`, `φ₂,₄'`, `φ₄,₇'`, `φ₈,₉'` and `φ₉,₆'` occur in the induced of the identity from the `A₂` corresponding to the  short  simple  roots;  the  pairs  (`φ₂,₁₆'`,  `φ₂,₄″`)  and (`φ₈,₃'`, `φ₈,₉″`)  are  related  by  tensoring  by  sign; and finally `φ₆,₆″` is the exterior  square of the  reflection representation. Note,  however, that we put  the long root at  the left of the  Dynkin diagrams to be in accordance with the conventions in [Lusztig1985, (4.8) and (4.10)](biblio.htm#Lus85).

The classes are labeled by Carter's admissible diagrams [Carter1972](biblio.htm#Car72).  A character  is labeled  by a pair `(d,b)` where  `d` denotes the  degree and `b`  the corresponding `b`-invariant. If there  are several characters with the same  pair `(d,b)` we attach a prime to them, as in [Carter1985](biblio.htm#Car85).

Types  `E₆,E₇,E₈`. The character  tables are obtained  by specialization of those  of the Hecke algebra. The classes are labeled by Carter's admissible diagrams [Carter1972](biblio.htm#Car72). A character is labeled by the pair `(d,b)`  where  `d`  denotes  the  degree  and  `b`  is  the  corresponding `b`-invariant.  For  these  types,  this  gives  a  unique  labeling of the characters.

Non-crystallographic  types `I₂(m)`, `H₃`, `H₄`. In these cases we do not have  canonical  labelings  for  the  classes.  We  label  them  by reduced expressions.

Each  character for  type `H₃`  is uniquely  determined by the pair `(d,b)` where  `d` is the degree and  `b` the corresponding `b`-invariant. For type `H₄`  there are just  two characters (those  of degree `30`)  for which the corresponding  pairs are  the same.  These two  characters are nevertheless distinguished  by  their  fake  degrees:  the  character `φ₃₀,₁₀'` has fake degree  `q¹⁰+q¹²+` higher terms, while `φ₃₀,₁₀″` has fake degree `q¹⁰+q¹⁴+` higher  terms. The characters in the table for type `H₄` are ordered in the same way as in [Alvis and Lusztig1982](biblio.htm#AL82).

Finally,  the characters  of degree `2`  for type  `I₂(m)` are  ordered as follows.  The matrix representations affording the characters of degree `2` are given by: $ρ_j : s₁s₂ ↦ \begin{pmatrix}\zeta_m^j&0\\0&\zeta_m^{-j}\end{pmatrix},  s₁↦\begin{pmatrix}0&1\\1&0\end{pmatrix},$ where  `1 ≤ j ≤  ⌊(m-1)/2⌋`. The reflection representation is  `ρ₁`. The  characters in  the table  are ordered by listing first the characters of degree 1 and then `ρ₁,ρ₂,…`.

Primitive complex reflection groups `G₄` to `G₃₄`. The  groups `G₂₃=H₃`, `G₂₈=F₄`, `G₃₀=H₄` are exceptional Coxeter groups and have  been  explained  above.  Similarly  for  the  other groups labels for characters  consist primarily  of the  pair `(d,b)`  where `d`  denotes the degree  and `b` is the corresponding  `b`-invariant. This is sufficient for `G₄`,  `G₁₂`, `G₂₂` and `G₂₄`. For other  groups there are pairs or triples of  characters which  have the  same `(d,b)`  value. We  disambiguate these according  to  the  conventions  of [Malle2000](biblio.htm#Mal00) for `G₂₇, G₂₉, G₃₁, G₃₃` and `G₃₄`:

  * For `G₂₇`:

The  fake degree  of `φ₃,₅'`  (resp. `φ₃,₂₀'`,  `φ₈,₉″`) has smaller degree that  of  `φ₃,₅″`  (resp.  `φ₃,₂₀″`,  `φ₈,₉'`). The characters `φ₅,₁₅'` and `φ₅,₆'` occur with multiplicity 1 in the induced from the trivial character of  the parabolic subgroup  of type `A₂`  generated by the  first and third generator  (it is asserted mistakenly in [Malle2000](biblio.htm#Mal00) that `φ₅,₆″` does not occur in this induced; it occurs with multiplicity 2).

  * For `G₂₉`:

The  character  `φ₆,₁₀‴`  is  the  exterior  square  of `φ₄,₁`; its complex conjugate  is `φ₆,₁₀⁗`. The  character `φ₁₅,₄″` occurs  in `φ₄,₁⊗φ₄,₃`; the character  `φ₁₅,₁₂″`  is  tensored  by  the  sign  character from `φ₁₅,₄″`. Finally  `φ₆,₁₀'` occurs in  the induced from  the trivial character of the standard parabolic subgroup of type `A₃` generated by the first, second and fourth generators.

  * For `G₃₁`:

The  characters `φ₁₅,₈'`, `φ₁₅,₂₀'` and `φ₄₅,₈″` occur in `φ₄,₁⊗φ₂₀,₇`; the character   `φ₂₀,₁₃'`  is  complex  conjugate  of  `φ₂₀,₇`;  the  character `φ₄₅,₁₂'`  is tensored by sign of `φ₄₅,₈'`. The two terms of maximal degree of  the fakedegree of `φ₃₀,₁₀'` are  `q⁵⁰+q⁴⁶` while for `φ₃₀,₁₀″` they are `q⁵⁰+2q⁴⁶`.

  * For `G₃₃`:

The two terms of maximal degree of the fakedegree of `φ₁₀,₈'` are `q²⁸+q²⁶` while  for `φ₁₀,₈″` they are `q²⁸+q²⁴`. The  terms of maximal degree of the fakedegree   of  `φ₄₀,₅'`  are  `q³¹+q²⁹`   while  for  `φ₄₀,₅″`  they  are `q³¹+2q²⁹`.  The character  `φ₁₀,₁₇'` is  tensored by  sign of `φ₁₀,₈'` and `φ₄₀,₁₄'` is tensored by sign of `φ₄₀,₅'`.

  * For `G₃₄`:

The  character `φ₂₀,₃₃'` occurs in `φ₆,₁⊗φ₁₅,₁₄`. The character `φ₇₀,₉'` is rational.  The character  `φ₇₀,₉″` occurs  in `φ₆,₁⊗φ₁₅,₁₄`.  The character `φ₇₀,₄₅'`   is  rational.The   character  `φ₇₀,₄₅″`   is  tensored  by  the determinant  character of  `φ₇₀,₉″`. The  character `φ₅₆₀,₁₈'` is rational. The character `φ₅₆₀,₁₈‴` occurs in `φ₆,₁⊗φ₃₃₆,₁₇`. The character `φ₂₈₀,₁₂'` occurs    in   `φ₆,₁⊗φ₃₃₆,₁₇`.   The   character   `φ₂₈₀,₃₀″`   occurs   in `φ₆,₁⊗φ₃₃₆,₁₇`.  The  character  `φ₅₄₀,₂₁'`  occurs  in `φ₆,₁⊗φ₁₀₅,₂₀`. The character  `φ₁₀₅,₈'` is  complex conjugate  of `φ₁₀₅,₄`,  and `φ₈₄₀,₁₃'` is complex  conjugate  of  `φ₈₄₀,₁₁`.  The  character  `φ₈₄₀,₂₃'`  is  complex conjugate  of  `φ₈₄₀,₁₉`.  Finally  `φ₁₂₀,₂₁'`  occurs  in induced from the trivial character of the standard parabolic subgroup of type `A₅` generated by the generators of `G₃₄` with the third one omitted.

For  the groups `G₅` and `G₇` we  adopt the following conventions. For `G₅` they are compatible with those of [MalleRouquier2003](biblio.htm#MR03) and [BroueMalleMichel2014](biblio.htm#BMM14).

  * For `G₅`:

We  let `W=complex_reflection_group(5)`,  so the  generators are  `W(1)` and `W(2)`.

The  character `φ₁,₄'` (resp. `φ₁,₁₂'`, `φ₂,₃'`) takes the value `1` (resp. `ζ₃`,  `-ζ₃`)  on  `W(1)`.  The  character  `φ₁,₈″` is complex conjugate to `φ₁,₁₆`,  and the character  `φ₁,₈'` is complex  conjugate to `φ₁,₄'` . The character  `φ₂,₅″` is complex conjugate to  `φ₂,₁`; `φ₂,₅'` takes the value `-1` on `W(1)`. The character `φ₂,₇'` is complex conjugate to `φ₂,₅'`.

  * For `G₇`:

We  let `W=complex_reflection_group(7)`,  so the  generators are `W(1)`, `W(2)` and `W(3)`.

The  characters  `φ₁,₄'`  and  `φ₁,₁₀'`  take  the value `1` on `W(2)`. The character  `φ₁,₈″` is complex  conjugate to `φ₁,₁₆`  and `φ₁,₈'` is complex conjugate  to `φ₁,₄'`. The characters `φ₁,₁₂'`  and `φ₁,₁₈'` take the value `ζ₃`  on `W(2)`. The character `φ₁,₁₄″` is complex conjugate to `φ₁,₂₂` and `φ₁,₁₄'`  is complex conjugate to `φ₁,₁₀'`. The character `φ₂,₃'` takes the value  `-ζ₃` on  `W(2)` and  `φ₂,₁₃'` takes  the value  `-1` on `W(2)`. The characters  `φ₂,₁₁″`, `φ₂,₅″`, `φ₂,₇‴` and  `φ₂,₁` are Galois conjugate, as well  as  the  characters  `φ₂,₇'`,  `φ₂,₁₃'`,  `φ₂,₁₁'`  and  `φ₂,₅'`. The character  `φ₂,₉'` is complex  conjugate to `φ₂,₁₅`  and `φ₂,₉‴` is complex conjugate to `φ₂,₃'`.

Finally,  for the remaining groups `G₆, G₈`  to `G₁₁, G₁₃` to `G₂₁`, `G₂₅`, `G₂₆`,  `G₃₂` and `G₃₃` there are only  pairs of characters with same value `(d,b)`.  We give labels uniformly to these characters by applying in order the following rules :

  * If the two characters have  different fake degrees, label `φ_{d,b}'` the  one  whose  fake  degree  is  minimal  for  the  lexicographic  order of  polynomials (starting with the highest term).
  * For the not yet labeled pairs, if only one of the two characters has the  property   that  in  its   Galois  orbit  at   least  one  character  is  distinguished by its `(d,b)`-invariant, label it `φ_{d,b}'`.
  * For the not yet labeled pairs,  if the minimum of the `(d,b)`-value (for  the  lexicographic  order  `(d,b)`)  in  the  Galois  orbits  of the two  character  is different, label `φ_{d,b}'` the character with the minimal  minimum.
  * We define now a new invariant  for characters: consider all the pairs of  irreducible   characters  `χ`  and  `ψ`  uniquely  determined  by  their  `(d,b)`-invariant such that `φ` occurs with non-zero multiplicity `m` in  `χ⊗ψ`.  We define  `t(φ)` to  be the  minimal (for  lexicographic order)  possible list `(d(χ),b(χ),d(ψ),b(ψ),m)`.

For  the not  yet labeled  pairs, if  the t-invariants are different, label `φ_{d,b}'` the character with the minimal `t`-invariant.

After  applying  the  last  rule  all  the  pairs  will be labelled for the considered  groups. The labelling obtained  is compatible for `G₂₅`, `G₂₆`, `G₃₂`  and `G₃₃`  with that  of [Malle2000](biblio.htm#Mal00)  and for `G₈` with that described in [MalleRouquier2003](biblio.htm#MR03).

We  should  emphasize  that  for  all  groups  with  a  few exceptions, the parameters  for characters do  not depend on  any non-canonical choice. The exceptions  are `G(de,e,n)` with `e>1`, and `G₅`, `G₇`, `G₂₇`, `G₂₈`, `G₂₉` and  `G₃₄`, groups  which admit  outer automorphisms  preserving the set of reflections,  so choices  of a  particular value  on a particular generator must be made for characters which are not invariant by these automorphisms.

Labels  for the classes. For the exceptional complex reflection groups, the labels  for the classes represent the  decomposition of a representative of the  class as a product of generators, with the additional conventions that 'z'  represents the generator  of the center  and for well-generated groups 'c'  represents a Coxeter element  (a product of the  generators which is a regular element for the highest reflection degree).

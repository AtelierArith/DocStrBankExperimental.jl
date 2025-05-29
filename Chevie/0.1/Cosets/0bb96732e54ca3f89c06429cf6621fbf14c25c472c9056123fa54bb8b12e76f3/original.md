Let  `R` be a  root system in  the real vector  space `V`. We say that `F₀∈ GL(V)`  is an  *automorphism of  `R`* if  it permutes  `R` and is of finite order  (finite  order  is  automatic  if  `R` generates `V`). It follows by [chap.  VI,  §1.1,  lemme  1  Bourbaki1968](biblio.htm#Bou68) that the dual `F₀*∈  GL(V*)`  permutes  the  coroots  `R*⊂  V*`; thus `F₀` normalizes the reflection  group  `W`  associated  to  `R`,  that  is  `w↦  F₀wF₀⁻¹` is an automorphism  of `W`. Thus we get a reflection coset `WF₀`, which we call a *Coxeter coset*.

The  motivation for introducing Coxeter  cosets comes from automorphisms of algebraic  reductive groups, giving rise to non-split reductive groups over finite fields. Let `𝐆` be a connected reductive algebraic group `𝐆` over an algebraic  closure `𝔽̄_q` of a finite field `𝔽_q`, defined over `𝔽_q`; this corresponds  to a  Frobenius endomorphism  `F` so  that the finite group of rational  points `𝐆(𝔽_q)` identifies to the  subgroup `𝐆^F` of fixed points under `F`.

Let `𝐓` be a maximal torus of `𝐆`, and `Φ` (resp. `Φ*`) be the roots (resp. coroots)  of `𝐆` with respect  to `𝐓` in the  character group `X(𝐓)` (resp. the  group of one-parameter subgroups `Y(𝐓)`). Then `𝐆` is determined up to isomorphism  by `(X(𝐓),Φ,Y(𝐓),Φ*)`; this corresponds  to give a root system in   the  vector  space  `V=ℚ ⊗ X(𝐓)`   and  a  rational  reflection  group `W=N_𝐆(𝐓)/𝐓` acting on it.

If  `𝐓` is `F`-stable the Frobenius endomorphism `F` acts also naturally on `X(T)`  and defines thus  an endomorphism of  `V`, which is  of the form `q F₀`, where `F₀∈ GL(V)` is of finite order and normalizes `W`. We get thus a Coxeter  coset `WF₀⊂GL(V)`.  The data  `(X(𝐓), Φ,  Y(𝐓), Φ*,  F₀)`, and the integer   `q`  completely  determine  up   to  isomorphism  the  associated *reductive finite group* `𝐆^F`. Thus these data is a way of representing in the  essential  information  which  determines  a  finite  reductive group. Indeed, all properties of Chevalley groups can be computed from that datum: symbols  representing characters, conjugacy classes,  and finally the whole character table of `𝐆^F`.

It  turns out that  many interesting objects  attached to this datum depend only on `(V,W, F₀)`: the order of the maximal tori, the *fake degrees*, the order  of `𝐆^F`, symbols representing unipotent characters, Deligne-Lusztig induction  in  terms  of  *almost  characters*, the Fourier matrix relating characters and almost characters, etc… (see, e.g., [Broue-Malle-Michel1993](biblio.htm#BMM93)).  It is thus possible to extend their  construction to non-crystallographic groups (or even to more general complex  reflection groups,  see [`spets`](@ref));  this is  why we did not include  a root  system in  the definition  of a reflection coset. However, unipotent conjugacy classes for instance depend on the root system.

We assume now that `𝐓` is contained in an `F`-stable Borel subgroup of `𝐆`. This  defines an order  on the roots,  and there is  a unique element `ϕ∈ W F₀`,  the  *reduced  element*  of  the  coset,  which  preserves the set of positive  roots.  It  thus  defines  a  *diagram  automorphism*, that is an automorphism  of the Coxeter system `(W,S)`.  This element is stored in the component  `.phi` of the coset record. It may be defined without mentioning the  roots,  as  follows:  `(W,F₀(S))`  is  another  Coxeter  system,  thus conjugate to `S` by a unique element of `W`, thus there is a unique element `ϕ∈  WF₀` which stabilizes `S` (a proof  follows from [Theoreme 1, chap. V, §3  Bourbaki1968](biblio.htm#Bou68)). We  consider thus  cosets of the form `Wϕ` where `ϕ` stabilizes `S`. The coset `W ϕ` is completely defined by the permutation  `.phi`  when  `𝐆`  is  semi-simple  –-  equivalently when `Φ` generates  `V`; in this  case we just  need to specify  `phi` to define the coset.

There is a slight generalisation of the above setup, covering in particular the  case of the Ree  and Suzuki groups. We  consider `𝐆^F` where `F` not a Frobenius  endomorphism, but  an isogeny  such that  some power  `F^n` is a Frobenius endomorphism. Then `F` still defines an endomorphism of `V` which normalizes  `W`; we define a real number `q` such that `F^n` is attached to an  `𝔽_{qⁿ}`-structure. Then we still have `F=q F₀` where `F₀` is of finite order  but `q` is no more an integer.  Thus `F₀∈ GL(V⊗ ℝ)` but `F₀∉ GL(V)`. For  instance, for the  Ree and Suzuki  groups, `F₀` is  an automorphism of order  `2` of `W`, which is of type `G₂`, `B₂` or `F₄`, and `q=√2` for `B₂` and  `F₄` and `q=√3`  for `G₂` This  can be constructed  starting from root systems  for `G₂`, `B₂` or  `F₄` where all the  roots have the same length. This kind of root system is *not* crystallographic. Such non-crystallographic  root systems exist for all finite Coxeter groups such as  the dihedral groups, `H₃` and `H₄`. We will call here *Weyl cosets* the cosets  corresponding to rational forms  of algebraic groups, which include thus some non-rational roots systems for `B₂`, `G₂` and `F₄`.

## Spets

We  now extend the above notions  to general complex reflection groups. Let `W⊂  GL(V)` be a complex reflection group  on the vector space `V`. Let `ϕ` be  an element  of `GL(V)`  which normalizes  `W`. Then  the coset  `Wϕ` is called a reflection coset.

A reference for these cosets is [Broue-Malle-Michel 1999](biblio.htm#BMM99). When `W` is a so-called *Spetsial* group, they are the basic object for the construction  of  a  *Spetses*,  which  is  an object attached to a complex reflection  group from which one can derive combinatorially some attributes shared with finite reductive groups, like unipotent degrees, etc….

We  say that  a reflection  coset is  irreducible if  `W` is irreducible. A general  coset is a direct  product of *descents of  scalars*, which is the case  where `ϕ`  is transitive  on the  irreducible components  of `W`. The irreducible    cosets   have   been   classified   in   [Broue-Malle-Michel 1999](biblio.htm#BMM99):  up to multiplication of `ϕ` by a scalar, there is usually only one or two possible cosets for a given irreducible group.

We  deal only  with *finite  order* cosets,  that is,  we assume there is a (minimal) integer `δ` such that `(Wϕ)^δ=W`. Then the group generated by `W` and `ϕ` is finite, of order `δ|W|`.

A  subset `C`  of a  `Wϕ` is  called a  *conjugacy class*  if one of the following equivalent conditions is fulfilled:

  * `C` is the orbit of an element in `Wϕ` under the conjugation action of `W`.
  * `C` is a conjugacy class of `⟨W,ϕ⟩` contained in `Wϕ`.
  * The set `{w∈ W|wϕ∈ C}` is  a `ϕ`-conjugacy  class of `W` (two elements

`v,w∈  W` are called `ϕ`-conjugate, if and only if there exists `x∈ W` with `v=xwϕ(x⁻¹)`).

An irreducible character of `⟨W,ϕ⟩` has some non-zero values on `Wϕ` if and only if its restriction to `W` is irreducible. Further, two characters `χ₁` and  `χ₂`  which  have  same  irreducible  restriction  to  `W` differ by a character  of  the  cyclic  group  `⟨ϕ⟩`  (which identifies to the quotient `⟨W,ϕ⟩/W`). A set containing one extension to `⟨W,ϕ⟩` of each `ϕ`-invariant character  of `W` is called a *set  of irreducible characters of `Wϕ`*. Two such  characters  are  orthogonal  for  the  scalar  product  on  the class functions on `Wϕ` given by $⟨χ,ψ⟩:=|W|¹∑_{w∈ W}χ(wϕ)\overline{ψ(wϕ)}.$ For rational groups (Weyl groups), Lusztig has defined a choice of a set of irreducible  characters for  `Wϕ` (called  the *preferred extensions*), but for  more  general  reflection  cosets  we  have made some rather arbitrary choices,  which  however  have  the  property  that their values lie in the smallest possible field.

The  *character  table*  of  `Wϕ`  is  the  table  of  values  of  a set of irreducible characters on the conjugacy classes.

A *subcoset* `Lwϕ` of `Wϕ` is given by a reflection subgroup `L` of `W` and an element `w` of `W` such that `wϕ` normalizes `L`.

We  then have a natural notion of  *restriction* of class functions on `Wϕ` to  class  functions  on  `Lwϕ`  as  well  as  of  *induction* in the other direction.  These  maps  are  adjoint  with  respect  to the scalar product defined above (see [Broue-Malle-Michel 1999](biblio.htm#BMM99)).

In  this package the most general construction  of a reflection coset is by starting  from a reflection datum, and giving in addition the matrix `F` of the  map `ϕ:V→ V`  (see the command  `spets`). However, at present, general cosets are only implemented for groups represented as permutation groups on a  set of roots, and  it is required that  the automorphism given preserves this  set up to  a scalar (it  is allowed that  these scalars depend on the pair  of an  irreducible component  and its  image). It  is also allowed to specify  `ϕ` by the permutation it induces on the roots; in this case it is assumed  that `ϕ` acts  trivially on the  orthogonal of the  roots, but the roots  could be those of a parent group, generating a larger space. Thus in any  case we have  a permutation representation  of `⟨W,ϕ⟩` and we consider the coset to be a set of permutations.

Reflection  cosets  are  implemented  in  by  a  `struct` which points to a reflection  group  record  and  has  additional  fields holding `F` and the corresponding  permutation `phi`. In the general case, on each component of `W`  which is  a descent  of scalars,  `F` will  permute the components and differ  by a scalar on each  component from an automorphism which preserves the  roots. In this case, we have  a permutation `phi` and a `scalar` which is stored for that component.

The  most common situation where cosets  with non-trivial `phi` arise is as sub-cosets  of reflection groups. Here is an "exotic" example, see the next chapter for more classical examples involving Coxeter groups.

```julia-repl
julia> W=complex_reflection_group(14)
G₁₄

julia> R=reflection_subgroup(W,[2,4])
G₁₄₍₂₄₎=G(-ζ₃²√-2)₅

julia> RF=spets(R,W(1))
G₁₄₍₂₄₎=²G(-ζ₃²√-2)₅
```

```julia-rep1
julia> diagram(RF)
ϕ acts as (1,2) on the component below
③ ══③ G₅
1   2
```

```julia-repl
julia> degrees(RF)
2-element Vector{Tuple{Int64, Cyc{Int64}}}:
 (6, 1)
 (12, -1)
```

The  last line shows for each  reflection degree the corresponding *factor* of  the coset, which is  the scalar by which  `ϕ` acts on the corresponding fundamental reflection invariant. The factors characterize the coset.

A  spets by default is  printed in an abbreviated  form which describes its type,  as above (`G₅` twisted by 2, with a Cartan matrix which differs from the  standard one by  a factor of  `√6`). The function  `repr` gives a form which could be input back in Julia. With the same data as above we have:

```julia-rep1
julia> print(RF)
spets(reflection_subgroup(complex_reflection_group(14),[2, 4]),perm"(1,3)(2,4)(5,9)(6,10)(7,11)(8,12)(13,21)(14,22)(15,23)(16,24)(17,25)(18,26)(19,27)(20,28)(29,41)(30,42)(31,43)(32,44)(33,45)(34,46)(35,47)(36,48)(37,49)(38,50)(39,51)(40,52)(53,71)(54,72)(55,73)(56,74)(57,75)(58,76)(59,77)(60,78)(62,79)(64,80)(65,81)(66,82)(67,69)(68,70)(83,100)(84,101)(85,102)(87,103)(89,99)(90,97)(91,98)(92,96)(93,104)(94,95)(105,113)(106,114)(109,111)(110,112)(115,118)(116,117)(119,120)")
```

Conjugacy  classes and irreducible characters of Coxeter cosets are defined as  for  general  reflection  cosets.  For  irreducible  characters of Weyl cosets,  we choose (following Lusztig) for each `ϕ`-stable character of `W` a  particular extension to a character of  `W⋊ ⟨ϕ⟩`, which we will call the *preferred extension*. The *character table* of the coset `Wϕ` is the table of  the restrictions to  `Wϕ` of the  preferred extensions. The question of finding the conjugacy classes and character table of a Coxeter coset can be reduced to the case of irreducible root systems `R`.

  * The automorphism `ϕ` permutes the irreducible components of `W`, and `Wϕ`  is a direct  product of cosets  where `ϕ` permutes cyclically the irreducible components of `W`. The preferred extension is defined to be the  direct  product  of  the  preferred  extension  in  each  of these situations.
  * Assume now that `Wϕ` is a descent of scalars, that is the decomposition in irreducible components `W=W₁× ⋯ × Wₖ` is cyclically permuted by `ϕ`. Then there are natural bijections from the `ϕ`-conjugacy classes of `W` to  the `ϕᵏ`-conjugacy classes  of `W₁` as  well as from the `ϕ`-stable characters  of `W` to the `ϕᵏ`-stable  characters of `W₁`, which reduce the  definition of preferred  extensions on `Wϕ`  to the definition for `W₁ϕᵏ`.
  * Assume now  that `W`  is the  Coxeter group  of an  irreducible root system.   `ϕ`  permutes  the  simple   roots,  hence  induces  a  graph automorphism  on  the  corresponding  Dynkin  diagram.  If  `ϕ=1`  then conjugacy  classes and  characters coincide  with those  of the Coxeter group `W`.

The  nontrivial cases for crystallographic roots  systems are (the order of `ϕ`  is written as left exponent to  the type): `²Aₙ`, `²Dₙ`, `³D₄`, `²E₆`. For  non-crystallographic root  systems where  all the  roots have the same length the additional cases `²B₂`, `²G₂`, `²F₄` and `²I₂(k)` arise.

  * In  case  `³D₄`  the  group  `W⋊ ⟨ϕ⟩`  can be embedded into the Coxeter  group of type `F₄`, which induces a labeling for the conjugacy classes of the coset. The preferred extension is chosen as the (single) extension with rational values.
  * In case  `²Dₙ` the  group `W⋊ ⟨ϕ⟩`  is isomorphic  to a Coxeter group of type `Bₙ`. This induces a canonical labeling for the conjugacy classes  of the coset and allows to define the preferred extension in a combinatorial  way  using  the  labels  (pairs  of  partitions) for the characters of the Coxeter group of type `Bₙ`.
  * In the remaining crystallographic cases `ϕ` identifies to `-w₀` where `w₀`  is the longest element of `W`.  So, there is a canonical labeling of  the conjugacy classes and characters of  the coset by those of `W`. The  preferred extensions  are defined  by describing  the signs of the character values on `-w₀`.

The  most general  construction of  a Coxeter  coset is  by starting from a Coxeter   datum   specified   by   the   matrices   of   `simpleRoots`  and `simplecoroots`,  and  giving  in  addition  the  matrix `F0Mat` of the map `F₀:V→ V` (see the commands  `CoxeterCoset` and `CoxeterSubCoset`). As for Coxeter  groups,  the  elements  of  `Wϕ`  are  uniquely  determined by the permutation  they  induce  on  the  set  of  roots  `R`.  We consider these permutations as `elements` of the Coxeter coset.

Coxeter  cosets are implemented by a struct which points to a Coxeter datum record  and  has  additional  fields  holding `F0Mat` and the corresponding element  `phi`. Functions on the coset (for example, `classinfo`) are about properties  of  the  group  coset  `W  ϕ`  ;  however, most definitions for elements of untwisted Coxeter groups apply without change to elements in `W ϕ`:  e.g., if we define the length of  an element `wϕ∈ Wϕ` as the number of positive  roots it sends to negative ones, it  is the same as the length of `w`,  i.e., `ϕ` is of length `0`, since `ϕ` has been chosen to preserve the set of positive roots. Similarly, the Coxeter `word` describing `wϕ` is the same as the one for `w`, etc…

We associate to a Coxeter coset `Wϕ` a *twisted Dynkin diagram*, consisting of  the Dynkin diagram of `W` and  the graph automorphism induced by `ϕ` on this  diagram (this  specifies the  group `W⋊  ⟨F⟩`, mentioned above, up to isomorphism).  See  the  functions  `refltype`,  `print`  and `diagram` for Coxeter cosets.

Below  is an example showing first how to *not* define, then how to define, the Weyl coset for a Suzuki group:

```julia-repl
julia> W=coxgroup(:B,2)
B₂

julia> spets(W,Perm(1,2))
ERROR: matrix F must preserve the roots
Stacktrace:
 [1] error(::String) at ./error.jl:33
 [2] spets(::Chevie.Weyl.FCG{Int16,Int64,PRG{Int64,Int16}}, ::Matrix{Int64}) at /home/jmichel/julia/Chevie/src/Cosets.jl:241 (repeats 2 times)
 [3] top-level scope at REPL[19]:1

julia> W=coxgroup(:Bsym,2)
Bsym₂

julia> WF=spets(W,Perm(1,2))
²Bsym₂

julia> CharTable(WF)
CharTable(²Bsym₂)
┌───┬─────────┐
│   │    1 121│
├───┼─────────┤
│2. │1   1   1│
│.11│1  -1  -1│
│1.1│. -√2  √2│
└───┴─────────┘
```

A *subcoset* `Hwϕ` of `Wϕ` is given by a reflection subgroup `H` of `W` and an  element `w` of `W`  such that `wϕ` induces  an automorphism of the root system of `H`. For algebraic groups, this corresponds to a rational form of a  reductive subgroup of maximal rank.  For example, if `Wϕ` corresponds to the  algebraic group `𝐆` and  `H` is the trivial  subgroup, the coset `Hwϕ` corresponds to a maximal torus `𝐓_w` of type `w`.

```julia-repl
julia> W=coxgroup(:Bsym,2)
Bsym₂

julia> WF=spets(W,Perm(1,2))
²Bsym₂

julia> subspets(WF,Int[],W(1))
²Bsym₂₍₎=Φ‴₈
```

A subgroup `H` which is a parabolic subgroup corresponds to a rational form of  a Levi  subgroup of  `𝐆`. The  command `twistings`  gives all rational forms of such a Levi.

```julia-repl
julia> W=coxgroup(:B,2)
B₂

julia> twistings(W,[1])
2-element Vector{Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}}:
 B₂₍₁₎=Ã₁Φ₁
 B₂₍₁₎=Ã₁Φ₂

julia> twistings(W,[2])
2-element Vector{Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}}:
 B₂₍₂₎=A₁Φ₁
 B₂₍₂₎=A₁Φ₂
```

Notice how we distinguish between subgroups generated by short roots and by long  roots. A general  `H` corresponds to  a reductive subgroup of maximal rank.  Here we consider the subgroup generated  by the long roots in `B₂`, which  corresponds to a  subgroup of type  `SL₂× SL₂` in `SP₄`, and show its possible rational forms.

```julia-repl
julia> W=coxgroup(:B,2)
B₂

julia> twistings(W,[2,4])
2-element Vector{Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}}:
 B₂₍₂₄₎=A₁×A₁
 B₂₍₂₄₎=(A₁A₁)
```

This   module  implements  Hecke  algebras  associated  to  finite  complex reflection  groups and arbitrary Coxeter  groups (these algebras are called Iwahori-Hecke  algebras  in  this  last  case),  and  also  implements  the character  tables, Schur elements and representations of Hecke algebras for finite  groups. For Iwahori-Hecke algebras  and `G(d,1,1)` this module also implements  the standard `T` basis;  see the module `KL`for Kazhdan-Lusztig bases.

Let  `(W,S)` be  a Coxeter  system and  let `mₛₜ`  be the order of `st` for `s,t∈ S`. Let `R` be a commutative ring with 1 and for `s∈ S` let `uₛ₀,uₛ₁∈ R` be elements which depend only on the conjugacy class of `s` in `W` (this is  the  same  as  requiring  that  `uₛᵢ=uₜᵢ`  whenever  `mₛₜ` is odd). The Iwahori-Hecke   algebra  of  `W`  over  `R`  with  parameters  `uₛᵢ`  is  a deformation  of the group algebra of `W` over `R` defined as follows: it is the  unitary  associative  `R`-algebra  generated  by  elements  `Tₛ, s∈ S` subject to the relations:

$(Tₛ-uₛ₀)(Tₛ-uₛ₁)=0$ for all `s∈ S` (the quadratic relations)

$TₛTₜTₛ…= TₜTₛTₜ…$ with `mₛₜ` factors on each side (the braid relations)

If  `uₛ₀=1` and  `uₛ₁=-1` for  all `s`  then the quadratic relations become `Tₛ²=1` and the deformation of the group algebra is trivial.

Since  the generators `Tₛ`  satisfy the braid  relations, `H` is  in fact a quotient  of the group algebra of the  braid group associated with `W`. The braid relations also imply that for any reduced expression `s_1⋯ s_m` of `w ∈  W` the product `Tₛ_1⋯ Tₛ_m` has the same value, that we denote `T_w`. We have `T_1=1`; if one of the `uₛᵢ` is invertible, the `{T_w}_{w∈ W}` form an `R`-basis  of the Iwahori-Hecke algebra  which specializes to the canonical basis of the group algebra `R[W]` for `uₛ₀↦1` and `uₛ₁↦-1`.

When  one  of  the  `uₛᵢ`  is  invertible,  the  structure  constants  (the decomposion  of  a  product  `T_vT_w`)  in  the `T_w` basis are obtained as follows.  Choose a reduced expression for `v`,  say `v=s_1 ⋯ s_k` and apply inductively the formula:

$T_sT_w=T_{sw}$               if `l(sw)=l(w)+1`

$T_sT_w=-uₛ₀uₛ₁T_{sw}+(uₛ₀+uₛ₁)T_w$ if `l(sw)=l(w)-1`.

If  one of `uₛ₀` or `uₛ₁` is invertible  in `R`, for example `uₛ₁`, then by changing  the generators  to `T′ₛ=-Tₛ/uₛ₁`,  and setting `qₛ=-uₛ₀/uₛ₁`, the braid  relations do no change  (since when `mₛₜ` is  odd we have `uₛᵢ=uₜᵢ`) but  the quadratic relations become `(T′ₛ-qₛ)(T′ₛ+1)=0`. This normalisation is  the most common form considered  in the literature. Another common form in  the context of  Kazhdan-Lusztig theory, is  `uₛ₀=√qₛ` and `uₛ₁=-√qₛ⁻¹`. The  form provided, with two parameters per generator, is often useful, for instance  when constructing  the Jones  polynomial. If  for all `s` we have `uₛ₀=q`,   `uₛ₁=-1`   then   we   call   the   corresponding   algebra  the "one-parameter" or "Spetsial" Iwahori-Hecke algebra associated with `W`.

For  some  Iwahori-Hecke  algebras  the  character  table,  and  in general Kazhdan-Lusztig  bases, require  a square  root of  `-uₛ₀uₛ₁`. These square roots  can be specified  with the keyword  `rootpara` when constructing the algebra;  after  this  the  function  `rootpara(H)`  will return the chosen roots. If not specified, we try to extract roots automatically when needed; `rootpara(H)`  informs  on  the  choices  made. Note that some mathematical results  require an explicit choice of one  of the two possible roots which cannot be automatically made thus require a keyword initialisation.

There  is a universal choice  for `R` and `uₛᵢ`:  Let `uₛᵢ:s∈ S,i∈[0,1]` be indeterminates   such  that  `uₛᵢ=uₜᵢ`  whenever  `mₛₜ`  is  odd,  and  let `A=ℤ[uₛᵢ]` be the corresponding polynomial ring. Then the Hecke algebra `H` of  `W` over `A` with parameters `uₛᵢ` is called the *generic Iwahori-Hecke algebra*  of  `W`.  Any  Hecke  algebra  `H₁`  with parameters `vₛᵢ` can be obtained  by  specialization  from  `H`,  since  there  is  a  unique  ring homomorphism  `f:A → R` such that `f(uₛᵢ)=vₛᵢ` for all `i`. Then via `f` we can identify `H₁` to $R⊗ _A H$.

Certain invariants of the irreducible characters of the one-parameter Hecke algebra  play a special role in the representation theory of the underlying finite  Coxeter  groups,  namely  the  `a`-  and  `A`-invariants. For basic properties   of  Iwahori-Hecke   algebras  and   their  relevance   to  the representation theory of finite groups of Lie type, see for example [Curtis and Reiner 1987](biblio.htm#CR87) Sections~67 and 68.

In  the  following  example,  we  compute  the multiplication table for the `0`-Iwahori–Hecke algebra associated with the Coxeter group of type `A_2`.

```julia-repl
julia> W=coxgroup(:A,2)
A₂

julia> H=hecke(W,0)            # One-parameter algebra with `q=0`
hecke(A₂,0)

julia> T=Tbasis(H);            # Create the `T` basis

julia> b=T.(elements(W))       # the basis
6-element Vector{HeckeTElt{HeckeAlgebra{Int64, Perm{Int16}, FiniteCoxeterGroup{Perm{Int16},Int64}}, Int64, Perm{Int16}}}:
 T.
 T₁
 T₂
 T₁₂
 T₂₁
 T₁₂₁

julia> b*permutedims(b)       # multiplication table
6×6 Matrix{HeckeTElt{HeckeAlgebra{Int64, Perm{Int16}, FiniteCoxeterGroup{Perm{Int16},Int64}}, Int64, Perm{Int16}}}:
 T.    T₁     T₂     T₁₂    T₂₁    T₁₂₁
 T₁    -T₁    T₁₂    -T₁₂   T₁₂₁   -T₁₂₁
 T₂    T₂₁    -T₂    T₁₂₁   -T₂₁   -T₁₂₁
 T₁₂   T₁₂₁   -T₁₂   -T₁₂₁  -T₁₂₁  T₁₂₁
 T₂₁   -T₂₁   T₁₂₁   -T₁₂₁  -T₁₂₁  T₁₂₁
 T₁₂₁  -T₁₂₁  -T₁₂₁  T₁₂₁   T₁₂₁   -T₁₂₁
```

Thus,  we work  with algebras  with arbitrary  parameters. We will see that this also works on the level of characters and representations.

For  general complex reflection  groups, the picture  is similar. The Hecke algebras  are deformations  of the  group algebras,  generalizing those for real reflection groups.

The  definition is  as a  quotient of  the algebra  of the  braid group. We assume  now that `W` is  a *finite* reflection group  in the complex vector space  `V`. The *braid group* associated  is the fundamental group `Π₁` of the  space  $(V-\bigcup_{H\in\mathcal H}  H)/W$, where $\mathcal H$ is  the set of  reflecting hyperplanes of  `W`. This group  is generated by *braid reflections*, elements which by the natural map from the braid group to  the reflection  group project  to distinguished  reflections. The braid reflections   which  project  to  a  given  `W`-orbit  of  reflections  are conjugate.  Let `𝐬` be a representative of  such a conjugacy class of braid reflections,  let `e`  be the  order of  the image  of `𝐬`  in `W`, and let $u_{𝐬,0},…,u_{𝐬,e-1}$ be indeterminates. The generic Hecke algebra of `W` is  the  $ℤ[u_{𝐬,i}^{±  1}]_{𝐬,i}$-algebra  quotient  of  the braid group algebra  by the relations $(𝐬-u_{𝐬,0})…(𝐬-u_{𝐬,e-1})=0$, and an arbitrary Hecke  algebra for `W` is an algebra  obtained from this generic algebra by specializing some of the parameters.

The  generic Hecke algebras are explicitely  described by a presentation of the  braid group. The braid group can be presented by homogeneous relations in   the  braid   reflections,  called   *braid  relations*,  described  in [Broué-Malle-Rouquier     1998](biblio.htm#BMR98)     and    [Bessis-Michel 2003](biblio.htm#BM03)  (some  of  which  were  obtained  using the VKCURVE GAP3-package,  also ported to Julia).  Furthermore, these presentations are such  that the  reflection group  is presented  by the same relations, plus relations  describing the order  of the generating  reflections, called the *order  relations*. Thus  the Hecke  algebra has  a presentation similar to that of `W`, with the same braid relations but the order relations replaced by a deformed version.

If  `S⊂ W`  is the  set of  distinguished reflections  of `W` which lift to generating  braid reflections in the braid  group, for each conjugacy class of  an  `s`  of  order  `e`  we take indeterminates `uₛ₀,…,uₛₑ₋₁`. Then the generic  Hecke algebra is the $ℤ[uₛᵢ^{±1}]ₛᵢ$-algebra `H` with generators `T_s`  for each `s∈  S` presented by  the braid relations  and the deformed order relations $(T_s-u_{s,0})…(T_s-u_{s,e-1})=0$.

Ariki,  Koike and Malle have computed the  character table of some of these algebras,  including  those  for  all  2-dimensional reflection groups, see [Broué-Malle 1993](biblio.htm#BM93) and [Malle 1996](biblio.htm#Mal96); our data  has  models  of  all  representation  and  character  tables for real reflection  groups; it  contains the  same for  imprimitive groups  and for primitive groups of dimension 2 and 3 (these last representations have been computed  in [Malle-Michel 2010](biblio.htm#MM10)) and contains also models and  character tables computed  by Michel for  `G₂₉` and `G₃₃`; it contains also  partial lists of representations and partial character tables for the remaining  groups `G₃₁,G₃₂`  and `G₃₄`,  computed by  Malle and  Michel for `G₃₂` and by Michel for the other two algebras.

The quotient of the Hecke algebra obtained by the specialisation $u_{𝐬,i}↦ ζₑⁱ$  is isomorphic to the group algebra of `W`. It was conjectured for 20 years  that over a splitting ring the Hecke algebra is itself isomorphic to the  group algebra of `W` over the  same ring. This was called the freeness conjecture since the main problem is to show that the Hecke algebra is free of dimension `|W|`. This has finally been proved in 2019 thanks to the work of  many  people  including  Marin,  Pfeiffer,  Chavli  and  Tsuchioka  for exceptional  groups. Along the way  it has been proven  that there exists a set  `{b_w}_{w∈ W}` of  elements of the  Braid group such  that `b_1=1` and `b_w` maps to `w` by the natural quotient map, such that their images `T_w` form a basis of the Hecke algebra.

It  is  conjectured  that  such  a  basis  `T_w`  can  be  chosen such that additionnaly  the  linear  form  `t`  defined  by  `t(T_w)=0` if `w≠ 1` and `t(1)=1` is a symmetrizing form for the symmetric algebra `H`. This is well known  for all real reflection groups  and has been proved in [Malle-Mathas 1998](biblio.htm#MM98)   for   imprimitive   reflection   groups   and   in [Malle-Michel 2010](biblio.htm#MM10) for some primitive groups of dimension 2  and  3.  Chlouveraki  and  Chavli  have handled some other 2-dimensional cases.  For  each  irreducible  character  `φ`  of `H` we define the *Schur element*  `Sᵩ` associated to `φ` by the  condition that for any element `T` of  `H` we have `t(T)=∑ᵩ φ(T)/Sᵩ`. It  can be shown that the Schur elements are  Laurent polynomials, and they  do not depend on  the choice of a basis having  the  above  property.  Malle  has  computed  these  Schur elements, assuming the above conjecture; they are in the Chevie data.

See the function `hecke` for various ways of specifying the parameters of a Hecke   algebra.  Look  also  at   the  docstrings  of  `central_monomials, char_values,     class_polynomials,    schur_elements,    isrepresentation, factorized_schur_elements`,  and  at  the  methods  for  Hecke  algebras of `CharTable, representations, reflrep`.

Taking  apart  Hecke  elements  is  done  with  the  functions  `getindex`, `setindex!`, `keys`, `values`, `iterate`.

```julia-repl
julia> H=hecke(W,Pol(:q))
hecke(A₂,q)

julia> T=Tbasis(H);

julia> h=T(1,2)^2
qT₂₁+(q-1)T₁₂₁

julia> length(h) # h has 2 terms
2

julia> h[W(2,1)] # coefficient of W(2,1)
Pol{Int64}: q

julia> collect(h) # pairs perm=>coeff
2-element Vector{Any}:
  (1,2,6)(3,4,5) => q
 (1,5)(2,4)(3,6) => q-1

julia> collect(values(h)) # the coefficients
2-element Vector{Pol{Int64}}:
 q
 q-1

julia> collect(keys(h)) # the corresponding Perms
2-element Vector{Perm{Int16}}:
 (1,2,6)(3,4,5)
 (1,5)(2,4)(3,6)

julia> h[W(2,1)]=Pol(3)
Pol{Int64}: 3

julia> h
3T₂₁+(q-1)T₁₂₁
```

finally, benchmarks on julia 1.8

```benchmark
julia> function test_w0(n)
         W=coxgroup(:A,n)
         Tbasis(hecke(W,Pol(:q)))(longest(W))^2
       end
test_w0 (generic function with 1 method)

julia> @btime test_w0(7);
   97.210 ms (1776476 allocations: 127.52 MiB)
```

in GAP3 the analogous function takes 920ms

```
test_w0:=function(n)local W,T,H;
  W:=CoxeterGroup("A",n);H:=Hecke(W,X(Rationals));T:=Basis(H,"T");
  return T(LongestCoxeterWord(W))^2;
end;
```

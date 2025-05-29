`split_levis(WF,ζ::Root1=1[,ad])`

Let  `WF`  be  a  reflection  group  or  a  reflection  coset.  If `W` is a reflection group it is treated as the trivial coset 'Spets(W)'. A  *Levi*  is  a  subcoset  of  the  form `W₁F₁` where `W₁` is a *parabolic subgroup* of `W`, that is the centralizer of some subspace of `V`, and `F₁∈ WF` normalizes `W₁`.

Let `ζ` be a root of unity. `split_levis` returns a list of representatives of  conjugacy classes  of `ζ`-split  Levis of  `W`. A  `ζ`-split Levi  is a subcoset  of `WF` formed  of all the  elements which act  by `ζ` on a given subspace  `V_ζ`. If the additional argument  `ad` is given, it returns only those subcosets such that the common `ζ`-eigenspace of their elements is of dimension  `ad`. These notions make sense  and thus are implemented for any complex reflection group.

In  terms of algebraic groups, an `F`-stable Levi subgroup of the reductive group  `𝐆`  is  `ζ`-split  if  and  only  if it is the centralizer of the `Φ`-part  of its center, where `Φ` is a cyclotomic polynomial with `ζ` as a root. When `ζ=1`, we get the notion of a *split* Levi, which is the same as a Levi sugroup of an `F`-stable parabolic subgroup of `𝐆`.

The  eigenvalue `ζ` can also  be specified by giving  an integer `d` (which then  specifies  `ζ=E(d)`)  or  a  fraction  `a//b`  which  then  specifies `ζ=E(b,a)`. If omitted, `ζ` is taken to be `1`.

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> split_levis(W,4)
2-element Vector{Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}}:
 A₃
 A₃₍₎=Φ₂Φ₄

julia> W=spets(coxgroup(:D,4),Perm(1,2,4))
³D₄

julia> split_levis(W,3)
3-element Vector{Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}}:
 ³D₄
 ³D₄₍₁₃₎=A₂Φ₃
 ³D₄₍₎=Φ₃²

julia> W=coxgroup(:E,8)
E₈

julia> split_levis(W,4,2)
3-element Vector{Spets{FiniteCoxeterSubGroup{Perm{Int16},Int64}}}:
 E₈₍₃₄₂₅₎=D₄₍₁₃₂₄₎Φ₄²
 E₈₍₅₇₂₃₎=(A₁A₁)×(A₁A₁)Φ₄²
 E₈₍₃₅₆₁₎=²(A₂A₂)₍₁₄₂₃₎Φ₄²

julia> split_levis(complex_reflection_group(5))
4-element Vector{Spets{PRSG{Cyc{Rational{Int64}}, Int16}}}:
 G₅
 G₅₍₁₎=G₃‚₁‚₁Φ₁
 G₅₍₂₎=G₃‚₁‚₁Φ₁
 G₅₍₎=Φ₁²
```

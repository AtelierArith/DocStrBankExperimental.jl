A  suitable  reference  for  the  general  theory of Coxeter groups is, for example, Bourbaki "Lie Groups and Lie Algebras" chapter 4.

A *Coxeter group* is a group which has the presentation $W=⟨S|(st)^{m(s,t)}=1\text{  for  }s,t∈  S⟩$  for some symmetric integer matrix `m(s,t)` called the *Coxeter matrix*, where `m(s,t)>1` for `s≠t` and `m(s,s)=1`;  `m(s,t)=∞` is allowed meaning there is no relation between `s` and `t`. It is true (but a non-trivial theorem) that in a Coxeter group the order  of `st` is exactly  `m(s,t)`, thus a Coxeter  group is the same as a *Coxeter  system*, that is a pair `(W,S)` of a group `W` and a set `S⊂W` of involutions,  such  that  the  group  is  presented  by  generators `S` and relations describing the order of the product of two elements of `S`.

A   Coxeter   group   has   a   natural   representation,  its  *reflection representation*, on a real vector space `V` of dimension `length(S)` (which is  the  *Coxeter  rank*  of  W),  where  each  element  of  `S`  acts as a reflection;  the faithfulness of this representation (a theorem of Tits) is the main argument to prove that the order of `st` is exactly `m(s,t)`. This representation  is defined as follows on a  space `V` with basis `{eₛ}` for `s∈  S`. The *cartan  matrix* associated to  the Coxeter matrix `m(s,t)` is the matrix `C` with entries `C(s,t)=-2cos(π/m(s,t))`; we set `C(s,t)=-2` if `m(s,t)=∞`. Then the action of `s∈ S` on `V` is given by `s(eₜ)=eₜ-C(s,t)eₛ`.

Thus, Coxeter groups are  real reflection groups.  The converse need not be true  if the set of reflecting  hyperplanes has bad topological properties, but  it turns out  that finite Coxeter  groups are the  same as finite real reflection  groups. The possible Coxeter matrices for finite Coxeter groups have  been  completely  classified,  see  [`Weyl`](@ref); the corresponding finite groups play a deep role in several areas of mathematics.

Coxeter  groups  have  a  nice  solution  to the word problem. The *length* `l(w)`  of an element  `w∈ W` is  the minimum number  of elements of `S` of which it is a product (since the elements of `S` are involutions, we do not need inverses). An expression of `w` of minimum length is called a *reduced word*  for `w`. The main property of  reduced words is the *exchange lemma* which  states that if `s₁…sₖ` is a reduced word for `w` (thus `k=l(w)`) and `s∈  S` is such that `l(sw)≤l(w)` then one  of the `sᵢ` in the word for `w` can be deleted to obtain a reduced word for `sw`. Thus given `s∈ S` and `w∈ W`,  either `l(sw)=l(w)+1` or `l(sw)=l(w)-1` and  in the latter case we say that `s` belongs to the *left descent set* of `w`. Computing a reduced word for  an  element,  and  other  word  problems,  are  easy if we know how to multiply elements and know left descent sets. In each of the Coxeter groups that we implement, the left descent set is easy to compute (see for example [`coxeter_symmetric_group`](@ref) below), so this suggests how to deal with Coxeter groups generically:

The  type  `CoxeterGroup`  is  an  abstract  type;  an  actual struct which implements it must define a function

`isleftdescent(W,w,i)` which tells whether the `i`-th element of `S` is in    the left descent set of `w`.

the other functions needed in an instance of a Coxeter group are

  * `gens(W)` which returns the set `S` (the list of *Coxeter generators*)
  * `nref(W)` which  returns the  number of  reflections of  `W`, if  `W` is  finite or `nothing` if `W` is infinite.

It  should  be  noted  that  a  Coxeter  group  can  be *any* kind of group implementing the above functions.

Because  of the  easy solution  of the  word problem  in Coxeter  groups, a convenient  way  to  represent  their  elements  is as words in the Coxeter generators,  that  is  lists  of  integers  in `1:length(S)`. The functions 'word'  and 'W(...)' do the conversion between Coxeter words and elements of the group.

# Examples

```julia-repl
julia> W=coxsym(4)
𝔖 ₄

julia> p=W(1,3,2,1,3)
(1,4)

julia> word(W,p)
5-element Vector{Int64}:
 1
 2
 3
 2
 1
```

We  notice that the word we started with and the one that we ended up with, are  not the same, even though they  represent the same element of `W`. The reason  is that there are several reduced  words for an element of `W`. The function 'word' calculates a lexicographically smallest word for `w`. Below are some other possible computations using the same Coxeter group:

```julia-repl
julia> word(W,longest(W))  # the (unique) longest element in W
6-element Vector{Int64}:
 1
 2
 1
 3
 2
 1

julia> w0=longest(W)
(1,4)(2,3)

julia> length(W,w0)
6
julia> map(w->word(W,w),refls(W,1:nref(W)))
6-element Vector{Vector{Int64}}:
 [1]
 [2]
 [3]
 [1, 2, 1]
 [2, 3, 2]
 [1, 2, 3, 2, 1]
julia> [length(elements(W,i)) for i in 0:nref(W)]
7-element Vector{Int64}:
 1
 3
 5
 6
 5
 3
 1
```

The  last list tells us that there is 1 element of length 0, there are 6 of length 3, …

For  most basic functions the convention is that the input is an element of the  group, rather than a  Coxeter word. The reason  for this is that for a Coxeter  group which is a permutation  group, using the low level functions for   permutations  is   usually  much   faster  than   manipulating  lists representing reduced expressions.

The only Coxeter group constructors implemented in this module are `coxsym` and  `coxgroup`; the last constructor takes  a Cartan matrix and builds the corresponding  Coxeter group as  a matrix group.  The module [`Weyl`](@ref) defines  other methods for `coxgroup` building  a finite Coxeter group as a permutation group, given its type.

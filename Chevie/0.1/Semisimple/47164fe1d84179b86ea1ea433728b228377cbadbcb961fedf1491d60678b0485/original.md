`algebraic_center(W)`

`W`  should  be  a  Weyl  group,  or  an extended Weyl group. This function returns  a description  of the  center `Z` of  the algebraic  group `𝐆` defined by `W` as a named tuple with the following fields:

`Z0`: the neutral component `Z⁰` of `Z` as a subtorus of `𝐓`.

`AZ`: representatives in `Z` of `A(Z):=Z/Z⁰` given as a group of semisimple elements.

`ZD`:  center of the derived subgroup of `𝐆` given as a group of semisimple elements.

`descAZ`:  if `W`  is not  an extended  Weyl group,  describes `A(Z)`  as a quotient  of the center  `pi` of the  simply connected covering  of `𝐆` (an incarnation of the fundamental group). It contains a list of elements given as  words  in  the  generators  of  `pi`  which  generate the kernel of the quotient map.

```julia_repl
julia> G=rootdatum(:sl,4)
sl₄

julia> L=reflection_subgroup(G,[1,3])
A₃₍₁₃₎=A₁×A₁

ulia> C=algebraic_center(L)
(Z0 = SubTorus(A₃₍₁₃₎=A₁×A₁Φ₁,[1 2 1]), AZ = Group(SemisimpleElement{Root1}[<1,1,-1>]), descAZ = [[1, 2]], ZD = Group(SemisimpleElement{Root1}[<-1,1,1>, <1,1,-1>]))

julia> G=coxgroup(:A,3)
A₃

julia> s=ss(G,[0,1//2,0])
SemisimpleElement{Root1}: <1,-1,1>

julia> C=centralizer(G,s)
A₃₍₁₃₎=(A₁A₁)Φ₂

julia> algebraic_center(C)
(Z0 = SubTorus(A₃₍₁₃₎=A₁×A₁Φ₁,Matrix{Int64}(undef, 0, 3)), AZ = Group(SemisimpleElement{Root1}[<1,-1,1>]))
```

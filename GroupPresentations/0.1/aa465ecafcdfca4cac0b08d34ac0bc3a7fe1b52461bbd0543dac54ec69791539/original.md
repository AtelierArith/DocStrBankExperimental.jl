This  is a  port of  some GAP3/VkCurve  functionality on *presentations* of *finitely presented groups*.

We  have defined just enough functionality  on finitely presented groups so that  presentations  can  be  translated  to  finitely presented groups and vice-versa. The focus is on presentations, the aim is to simplify them.

The  elements of finitely presented groups are `AbsWord` or abstract words, representing elements of a free group. 

```julia-repl
julia> @AbsWord a,b,c,d,e,f # same as a=AbsWord(:a);b=AbsWord(:b)...

julia> F=FpGroup([a,b,c,d,e,f])
FreeGroup(a,b,c,d,e,f)

julia> G=F/[a^2,b^2,d*f^-1,e^2,f^2,a*b^-1*c,a*e*c^-1,b*d^-1*c,c*d*e^-1,a*f*c^-2,c^4]
FreeGroup(a,b,c,d,e,f)/[a²,b²,df⁻¹,e²,f²,ab⁻¹c,aec⁻¹,bd⁻¹c,cde⁻¹,afc⁻²,c⁴]

julia> simplify(F) # the main function of this package
Presentation: 2 generators, 4 relators, total length 16
Presentation: 2 generators, 3 relators, total length 10
FreeGroup(a,c)/[a²,ac⁻¹ac⁻¹,c⁴]
```

The simplification is done by the following process:

```julia-rep1
julia> P=Presentation(G);simplify(P);G=FpGroup(P)
```

The  functions `Presentation`  and `FpGroup`  create a  presentation from a finitely presented group and vice versa.

In order to speed up the algorithms, the relators in a presentation are not represented  internally by `AbsWord`s, but by lists of positive or negative generator  numbers which  we call  *Tietze words*.  Here is another example with a few functions to explore presentations.

```julia-repl
julia> @AbsWord a,b 

julia> F=FpGroup([a,b])
FreeGroup(a,b)

julia> G=F/[a^2,b^7,comm(a,a^b),comm(a,a^(b^2))*inv(b^a)]
FreeGroup(a,b)/[a²,b⁷,a⁻¹b⁻¹a⁻¹bab⁻¹ab,a⁻¹b⁻²a⁻¹b²ab⁻²ab²a⁻¹b⁻¹a]

julia> P=Presentation(G) # by default give a summary
Presentation: 2 generators, 4 relators, total length 30

julia> relators(P)
4-element Vector{AbsWord}:
 a²
 b⁷
 ab⁻¹abab⁻¹ab
 b⁻²ab²ab⁻²ab²ab⁻¹
```

```julia-rep1
julia> showgens(P)
1. a 10 occurrences involution
2. b 20 occurrences

julia> dump(P) # here in relators inverses are represented by capitalizing
# F relator
1:3 aa
2:0 bbbbbbb
3:0 aBabaBab
4:0 abbaBBabbaBBB
gens=AbsWord[a, b] involutions:AbsWord[a] modified=false numredunds=0

julia> display_balanced(P)
1: a=A
2: bbbbbbb=1
3: aBab=BAbA
4: BBabbaBBabbaB=1

julia> P=tryconjugate(P) # try to conjugate the generators
Presentation: 2 generators, 4 relators, total length 30
Bab=> Presentation: 2 generators, 3 relators, total length 28
# Bab gives Presentation: 2 generators, 3 relators, total length 28
Presentation: 2 generators, 3 relators, total length 28

julia> FpGroup(P) # slightly simplified group
FreeGroup(a,b)/[b⁷,bab⁻¹abab⁻¹a,b⁻¹ab²ab⁻²ab²ab⁻²]
```

for  more  information  look  at  the  help  strings  of `AbsWord, FpGroup, Presentation,     relators,    display_balanced,    simplify,    conjugate, tryconjugate`. 

A  minimal thing to add to this package so it would be a reasonable package for finitely preented groups is the Coxeter-Todd algorithm.

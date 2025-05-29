`Presentation(M::GarsideMonoid)`

returns  a presentation of  the Garside group  defined by `M`  (as given in theorem 4.1 of [Dehornoy-Paris 1999](biblio.htm#DePa99)).

```julia-repl
julia> M=DualBraidMonoid(coxgroup(:A,3))
DualBraidMonoid(A₃,c=[1, 3, 2])

julia> p=Presentation(M)
Presentation: 6 generators, 15 relators, total length 62
```

```julia-rep1
julia> simplify(p)
<< presentation with 3 generators, 4 relators of total length 26>>
<< presentation with 3 generators, 3 relators of total length 16>>

julia> display_balanced(p)
1: ab=ba
2: cac=aca
3: cbc=bcb
```

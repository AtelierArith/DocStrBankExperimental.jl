`bruhatPoset(W::CoxeterGroup,w=longest(W))`

returns  as a poset the Bruhat interval `[1,w]`of `W`. If `w` is not given, the whole Bruhat Poset of `W` is returned (`W` must then be finite).

```julia-repl
julia> W=coxsym(3)
𝔖 ₃

julia> bruhatPoset(W)
.<1,2<21,12<121
```

The  above  poset  is  constructed  efficiently  by  constructing the Hasse diagram, but it could be constructed naively as follows:

```julia-repl
julia> p=Poset((x,y)->bruhatless(W,x,y),elements(W))
()<(1,2),(2,3)<(1,3,2),(1,2,3)<(1,3)
```

The  output is not so nice, showing permutations instead of words. This can be fixed by defining:

```julia-repl
julia> p.show_element=(io,x,n)->join(io,word(W,x.elements[n]));

julia> p
<1,2<12,21<121

julia> W=coxsym(4)
𝔖 ₄

julia> bruhatPoset(W,W(1,3))
.<3,1<13
```

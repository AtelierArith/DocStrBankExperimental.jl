`centralizer(W,s::SemisimpleElement)`

`W`  should  be  a  Weyl  group  or  an extended reflection group and `s` a semisimple  element of the  algebraic group `G`  corresponding to `W`. This function  returns the  Weyl group  of $C_G(s)$,  which describes  it. The stabilizer  is an extended reflection group, with the reflection group part equal to the Weyl group of $C_{G⁰}(s)$, and the diagram automorphism part being those induced by $C_G(s)$.

```julia-repl
julia> G=coxgroup(:A,3)
A₃
julia> s=ss(G,[0,1//2,0])
SemisimpleElement{Root1}: <1,-1,1>
julia> centralizer(G,s)
A₃₍₁₃₎=(A₁A₁)Φ₂
```

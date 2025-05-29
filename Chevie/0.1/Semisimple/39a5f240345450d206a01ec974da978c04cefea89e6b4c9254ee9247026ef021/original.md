`quasi_isolated_reps(W,p=0)`

`W`  should be a Weyl  group corresponding to an  algebraic group 𝐆 over an algebraically  closed field  of characteristic  0. This  function returns a list  of  semisimple  elements  for  𝐆,  which  are  representatives of the 𝐆-orbits  of quasi-isolated  semisimple elements.  It follows the algorithm given  in  [Bonnafe2005](biblio.htm#Bon05).  If  a  second  argument `p` is given,  it  gives  representatives  of  those quasi-isolated elements which exist in characteristic `p`.

```julia-repl
julia> W=coxgroup(:E,6);l=quasi_isolated_reps(W)
5-element Vector{SemisimpleElement{Root1}}:
 <1,1,1,1,1,1>
 <1,-1,1,1,1,1>
 <1,1,1,ζ₃,1,1>
 <ζ₃,1,1,1,1,ζ₃>
 <1,ζ₆,ζ₆,1,ζ₆,1>

julia> map(s->isisolated(W,s),l)
5-element Vector{Bool}:
 1
 1
 1
 0
 0

julia> W=rootdatum(:E6sc);l=quasi_isolated_reps(W)
7-element Vector{SemisimpleElement{Root1}}:
 <1,1,1,1,1,1>
 <-1,1,1,-1,1,-1>
 <ζ₃,1,ζ₃²,1,ζ₃,ζ₃²>
 <ζ₃²,1,ζ₃,1,ζ₃,ζ₃²>
 <ζ₃²,1,ζ₃,1,ζ₃²,ζ₃>
 <ζ₆⁵,1,ζ₃²,1,ζ₃,ζ₃²>
 <ζ₃²,1,ζ₃,1,ζ₃²,ζ₆⁵>

julia> map(s->isisolated(W,s),l)
7-element Vector{Bool}:
 1
 1
 1
 1
 1
 1
 1

julia> Semisimple.quasi_isolated_reps(W,3)
2-element Vector{SemisimpleElement{Root1}}:
 <1,1,1,1,1,1>
 <-1,1,1,-1,1,-1>
```

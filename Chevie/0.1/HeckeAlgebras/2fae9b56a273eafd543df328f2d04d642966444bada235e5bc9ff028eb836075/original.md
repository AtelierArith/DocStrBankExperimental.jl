`reflection_representation(H::HeckeAlgebra)` or `reflrep(H)`

returns  a  list  of  matrices  for  the  generators  of `H` which give the reflection representation of the Iwahori-Hecke algebra `H`.

```julia-repl
julia> W=coxgroup(:B,2);H=hecke(W,Pol(:q))
hecke(B₂,q)

julia> reflrep(H)
2-element Vector{Matrix{Pol{Int64}}}:
 [-1 0; -q q]
 [q -2; 0 -1]

julia> H=hecke(coxgroup(:H,3))
hecke(H₃,1)

julia> reflrep(H)
3-element Vector{Matrix{Cyc{Int64}}}:
 [-1 0 0; -1 1 0; 0 0 1]
 [1 (-3-√5)/2 0; 0 -1 0; 0 -1 1]
 [1 0 0; 0 1 -1; 0 0 -1]
```

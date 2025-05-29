`isrepresentation(H::HeckeAlgebra,r)`

returns `true` or `false`, according to whether a given set `r` of elements corresponding  to  the  standard  generators  of the reflection group `H.W` defines a representation of the Hecke algebra `H` or not.

```julia-repl
julia> H=hecke(coxgroup(:F,4))
hecke(F₄,1)

julia> isrepresentation(H,reflrep(H))
true

julia> isrepresentation(H,Tbasis(H).(1:4))
true
```

`representations(H)`

returns  the list  of representations  of the  Hecke algebra or Hecke coset `H` (see `representation`).

```julia-repl
julia> WF=rootdatum("2B2")
²B₂

julia> H=hecke(WF,Pol(:x)^2;rootpara=Pol())
hecke(²B₂,x²,rootpara=x)

julia> representations(H)
3-element Vector{NamedTuple{(:gens, :F)}}:
 (gens = Matrix{Pol{Int64}}[[x²;;], [x²;;]], F = [1;;])
 (gens = Matrix{Pol{Int64}}[[-1;;], [-1;;]], F = [1;;])
 (gens = Matrix{Pol{Cyc{Int64}}}[[-1 0; √2x x²], [x² √2x; 0 -1]], F = [0 -1; -1 0])
```

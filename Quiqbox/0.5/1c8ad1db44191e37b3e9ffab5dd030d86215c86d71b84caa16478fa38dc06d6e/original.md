```
changeMapping(pb::ParamBox{T, V}, mapFunction::Function=itself, outSym::Symbol=V; 
              canDiff::Union{Bool, Array{Bool, 0}}=isDiffParam(pb)) where {T, V} -> 
ParamBox{T, outSym}
```

Change the mapping function of `pb`. The symbol of the output variable of the returned  `ParamBox` can be specified by `outSym`, and its differentiability is determined by  `canDiff`.

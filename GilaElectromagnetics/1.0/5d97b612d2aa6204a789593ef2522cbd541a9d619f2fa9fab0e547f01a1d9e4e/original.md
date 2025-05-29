```
function GlaOprMem(cmpInf::GlaKerOpt, trgVol::GlaVol,
srcVol::Union{GlaVol,Nothing}=nothing, 
egoFur::Union{AbstractArray{<:AbstractArray{T}},
Nothing}=nothing)::GlaOprMem where T<:Union{ComplexF64,ComplexF32}
```

Prepare memory for green function operator–-when called with a single GlaVol,  or identical source and target volumes, yields the self construction. 

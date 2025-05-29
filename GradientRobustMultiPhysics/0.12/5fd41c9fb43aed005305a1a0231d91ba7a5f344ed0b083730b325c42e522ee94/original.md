```
function evaluate(
    AP::AssemblyPattern{APT,T,AT},
    FEB::Union{<:FEVector{T,Tv,Ti},<:FEVectorBlock{T,Tv,Ti},Array{<:FEVectorBlock{T,Tv,Ti},1}};
    skip_preps::Bool = false) where {APT <: APT_ItemIntegrator, T<: Real, AT <: AssemblyType, Tv, Ti}

```

Evaluation of an ItemIntegrator assembly pattern with given FEVectorBlock or FEVector FEB, only returns accumulation over all items.

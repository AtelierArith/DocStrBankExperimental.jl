```
function evaluate(
    AP::AssemblyPattern{APT,T,AT},
    FEB::Union{<:FEVector{T,Tv,Ti},<:FEVectorBlock{T,Tv,Ti},Array{<:FEVectorBlock{T,Tv,Ti},1}};
    skip_preps::Bool = false) where {APT <: APT_ItemIntegrator, T<: Real, AT <: AssemblyType, Tv, Ti}

```

与えられた FEVectorBlock または FEVector FEB に対する ItemIntegrator アセンブリパターンの評価は、すべてのアイテムに対する累積のみを返します。

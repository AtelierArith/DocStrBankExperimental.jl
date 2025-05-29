```
const MultilineMPS = Multiline{<:InfiniteMPS}
```

`InfiniteMPS`オブジェクトの複数行を表す型です。

# コンストラクタ

```
MultilineMPS(mpss::AbstractVector{<:InfiniteMPS})
MultilineMPS([f, eltype], physicalspaces::Matrix{<:Union{S, CompositeSpace{S}},
             virtualspaces::Matrix{<:Union{S, CompositeSpace{S}}) where
             {S<:ElementarySpace}
MultilineMPS(As::AbstractMatrix{<:GenericMPSTensor}; kwargs...)
MultilineMPS(ALs::AbstractMatrix{<:GenericMPSTensor}, 
             C₀::AbstractVector{<:MPSBondTensor}; kwargs...)
```

参照: [`Multiline`](@ref)

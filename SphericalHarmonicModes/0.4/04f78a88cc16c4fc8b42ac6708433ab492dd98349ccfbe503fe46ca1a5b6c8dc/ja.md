```
ML(l_range::Union{Integer, AbstractUnitRange{<:Integer}}, m_range::Union{Integer, AbstractUnitRange{<:Integer}})
ML(l_range::Union{Integer, AbstractUnitRange{<:Integer}}, [T = FullRange]) where T<:Union{FullRange, ZeroTo, ToZero}
```

ペアの球面調和モード `(l,m)` をループするイテレータを返します。ここで `m` は `l` よりも速く増加します。ループは、提供された範囲から得られるすべての有効なモードを対象とします。 `m_range` が指定されていない場合、ループは各 `l` に対して有効な `m` のすべての値を対象とします。 `l_range` と `m_range` は空であってはなりません。

オプションとして、`m_range` は範囲指定子 [`FullRange`](@ref)、[`ZeroTo`](@ref)、および [`ToZero`](@ref) を使用して暗黙的に提供することができます。または、[`SingleValuedRange`](@ref) 型として提供することもできます。さらに、`l_range` は [`ZeroTo`](@ref) または [`SingleValuedRange`](@ref) 型である場合があります。これらの特別な型を使用して構築されたイテレータは、最適化を許可することがよくあります。

!!! warning
    大きすぎる `l_range` は、`m_range` と互換性のある有効な範囲に合わせて制限されます。 `m_range` と互換性のない小さな `l_range` はエラーを引き起こします。


# 例

```jldoctest
julia> ML(0:1) |> collect
4-element Vector{Tuple{Int64, Int64}}:
 (0, 0)
 (1, -1)
 (1, 0)
 (1, 1)

julia> ML(0:1, 1:1) |> collect
1-element Vector{Tuple{Int64, Int64}}:
 (1, 1)

julia> r = ML(ZeroTo(1), FullRange);

julia> r |> collect
4-element Vector{Tuple{Int64, Int64}}:
 (0, 0)
 (1, -1)
 (1, 0)
 (1, 1)
```

参照: [`LM`](@ref) ```

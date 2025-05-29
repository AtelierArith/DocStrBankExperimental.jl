```
bags(k::Vector{<:Integer})
bags(k::Vector{T}) where T <: UnitRange{<:Integer}
bags(b::AbstractBags)
```

入力に最も適した[`AbstractBags`](@ref)構造体を構築します（可能であれば[`AlignedBags`](@ref）、そうでなければ[`ScatteredBags`](@ref)）。

# 例

```jldoctest
julia> bags([1, 1, 3])
AlignedBags{Int64}(UnitRange{Int64}[1:2, 0:-1, 3:3])

julia> bags([2, 3, 1, 2])
ScatteredBags{Int64}([[3], [1, 4], [2]])

julia> bags([1:3, 4:5])
AlignedBags{Int64}(UnitRange{Int64}[1:3, 4:5])

julia> bags(ScatteredBags())
ScatteredBags{Int64}(Vector{Int64}[])
```

関連情報: [`AlignedBags`](@ref), [`ScatteredBags`](@ref).

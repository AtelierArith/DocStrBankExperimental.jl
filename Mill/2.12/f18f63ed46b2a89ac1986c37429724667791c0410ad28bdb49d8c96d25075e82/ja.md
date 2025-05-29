```
LazyNode([Name::Symbol], d, m=nothing)
LazyNode{Name}(d, m=nothing)
```

新しい[`LazyNode`](@ref)を名前`Name`、データ`d`、およびメタデータ`m`で構築します。

# 例

```jldoctest
julia> LazyNode(:Codons, ["GGGCGGCGA", "CCTCGCGGG"])
LazyNode{:Codons, Vector{String}, Nothing}:
 "GGGCGGCGA"
 "CCTCGCGGG"
```

参照: [`AbstractMillNode`](@ref), [`LazyModel`](@ref), [`Mill.unpack2mill`](@ref).

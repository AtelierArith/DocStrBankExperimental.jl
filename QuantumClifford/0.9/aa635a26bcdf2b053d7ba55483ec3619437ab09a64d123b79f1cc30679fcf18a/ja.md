基礎的なタブロー構造を抽出します。

```jldoctest
julia> s = S"X"
+ X

julia> tab(s)
+ X

julia> tab(Destabilizer(s))
+ Z
+ X

julia> tab(MixedDestabilizer(s))
+ Z
+ X

julia> tab(tHadamard)
+ Z
+ X

julia> typeof(tab(tHadamard))
QuantumClifford.Tableau{Vector{UInt8}, Matrix{UInt64}}
```

参照: [`stabilizerview`](@ref), [`destabilizerview`](@ref), [`logicalxview`](@ref), [`logicalzview`](@ref)

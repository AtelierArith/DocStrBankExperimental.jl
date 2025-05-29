```
LazyTree(f::ROOTFile, s::AbstractString, branch::Union{AbstractString, Regex})
LazyTree(f::ROOTFile, s::AbstractString, branch::Vector{Union{AbstractString, Regex}})
```

`LazyTree`のコンストラクタで、`DataFrame`に近い（インターフェース的に）かつ、遅延テーブル（速度的に）です。`LazyTree`をループするのは速く、型が安定しています。内部的に、`LazyTree`は[`LazyBranch`](@ref)を持つ型付きテーブルを含んでいます。これは、任意の時点で`N`個のバスケットのみがキャッシュされていることを意味し、`N`はブランチの数です。

!!! note
    `[start:stop]`でアクセスすると、具体的な内部テーブルを持つ`LazyTree`が返されます。


!!! warning
    分割されたブランチは再命名され、正確な再命名は変更される可能性があります。詳細については、[Issue 156](https://github.com/JuliaHEP/UnROOT.jl/pull/156)を参照してください。


# 例

```julia
julia> mytree = LazyTree(f, "Events", ["Electron_dxy", "nMuon", r"Muon_(pt|eta)$"])
 Row │ Electron_dxy     nMuon   Muon_eta         Muon_pt
     │ Vector{Float32}  UInt32  Vector{Float32}  Vector{Float32}
─────┼───────────────────────────────────────────────────────────
 1   │ [0.000371]       0       []               []
 2   │ [-0.00982]       2       [0.53, 0.229]    [19.9, 15.3]
 3   │ []               0       []               []
 4   │ [-0.00157]       0       []               []
 ⋮   │     ⋮            ⋮             ⋮                ⋮
```

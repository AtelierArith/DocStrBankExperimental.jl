```
ROOTFile(filename::AbstractString; customstructs = Dict("TLorentzVector" => LorentzVector{Float64}))
```

`ROOTFile`のコンストラクタはファイルから作成されます。`customstructs`辞書は、ユーザー定義の構造体を値として渡し、その対応する`fClassName`（Branch内）をキーとして使用するために利用でき、`UnROOT`がそれらを解釈することを知ることができます。詳細は[`interped_data`](@ref)を参照してください。

関連情報: [`LazyTree`](@ref), [`LazyBranch`](@ref)

# 例

```julia
julia> f = ROOTFile("test/samples/NanoAODv5_sample.root")
ROOTFile with 2 entries and 21 streamers.
test/samples/NanoAODv5_sample.root
└─ Events
   ├─ "run"
   ├─ "luminosityBlock"
   ├─ "event"
   ├─ "HTXS_Higgs_pt"
   ├─ "HTXS_Higgs_y"
   └─ "⋮"
```

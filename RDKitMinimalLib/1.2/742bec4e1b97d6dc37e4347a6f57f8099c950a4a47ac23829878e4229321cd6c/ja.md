```
get_rxn(rxn_string::AbstractString, details::Union{Dict{String,Any},Nothing}=nothing)::Union{Reaction,Nothing}
```

SMARTSから反応オブジェクトを取得します。現在は描画目的でのみ使用できます。

```julia
rxn = get_rxn("[CH3:1][OH:2]>>[CH2:1]=[OH0:2]")
```

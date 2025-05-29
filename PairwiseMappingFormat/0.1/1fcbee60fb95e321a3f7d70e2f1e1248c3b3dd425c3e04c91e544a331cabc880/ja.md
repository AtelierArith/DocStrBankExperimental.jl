```
aux_data(rec::Record) -> XAMAuxData.SAM.Auxiliary
```

レコードの最後にある補助フィールドの `AbstractDict` である `SAM.Auxiliary` を遅延評価および検証して返します。このオブジェクトの詳細については、パッケージ XAMAuxData.jl のドキュメントを参照してください。

# 例

```jldoctest
julia> aux = aux_data(record);

julia> length(aux)
4

julia> aux["cm"]
29990

julia> aux["k1"] = "add a new aux string like this";

julia> haskey(aux, "k1")
true
```

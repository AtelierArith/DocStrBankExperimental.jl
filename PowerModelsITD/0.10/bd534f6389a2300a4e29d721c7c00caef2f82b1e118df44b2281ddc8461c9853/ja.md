```
function remove_all_bounds!(
    pmitd_data::Dict{String,<:Any};
    exclude::Vector{<:String}=String["energy_ub"]
)
```

対応する変換を適用し、数学モデルによって必要とされていないすべてのフィールドを削除します。削除から除外するプロパティは `exclude::Vector{String}` で指定できます。デフォルトでは、ストレージに必要なプロパティである `"energy_ub"` はこの削除から除外されます（pmd内）。

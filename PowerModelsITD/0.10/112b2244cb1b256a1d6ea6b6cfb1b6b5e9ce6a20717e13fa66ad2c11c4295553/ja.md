```
function apply_kron_reduction!(
    pmitd_data::Dict{String,<:Any}
)
```

ネットワークにKron Reductionを適用する対応する変換を適用し、`kr_neutral`を削除し、`kr_phases`のみを残します。

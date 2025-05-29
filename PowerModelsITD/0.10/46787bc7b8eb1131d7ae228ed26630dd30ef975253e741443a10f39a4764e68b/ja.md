```
function calc_transmission_branch_flow_ac!(
    result::Dict{String,<:Any},
    pmitd_data::Dict{String,<:Any};
)
```

有効なACソリューションが結果に含まれていると仮定し、ブランチフロー値を計算します。`result`辞書ではなく、`pmitd_data`辞書内にPFソリューションを返します。_PM関数を複製しますが、PMITD辞書と互換性があります。

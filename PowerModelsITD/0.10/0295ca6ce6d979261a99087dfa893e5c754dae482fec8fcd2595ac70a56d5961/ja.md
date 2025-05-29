```
function transform_pmitd_solution_to_eng!(
    result::Dict{String,<:Any},
    pmitd_data::Dict{String,<:Any}
)
```

PMITDソリューションをMATHモデルからENGモデルに変換します。この変換は、ENGモデルに従ってバス番号をバス名に変換する「pmitd」での変換を容易にします。例: (100002, 9, 6) -> (100002, voltage*source.3bus*unbal*nogen*mn_2.source, 6)

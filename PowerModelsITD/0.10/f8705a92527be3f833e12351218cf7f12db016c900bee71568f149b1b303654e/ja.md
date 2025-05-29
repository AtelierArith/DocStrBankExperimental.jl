```
function sol_data_model!(
    pmitd::AbstractPowerModelITD,
    solution::Dict{String,<:Any}
)
```

solution_processorは、解を極座標電圧の大きさと角度に変換します。

```
mean_and_se(v::AbstractVector; α = 0.01, corrected::Bool=true, skip=0) -> mean, err
mean_and_se(r::BlockingResult) -> mean, err
```

[`blocking_analysis`](@ref)から得られた時系列の平均と標準誤差をタプルとして返します。[`BlockingResult`](@ref)も参照してください。

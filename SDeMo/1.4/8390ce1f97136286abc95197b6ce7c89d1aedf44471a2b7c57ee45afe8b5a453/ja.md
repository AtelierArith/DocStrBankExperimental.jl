```
variables!(model::M, ::Type{StrictVarianceInflationFactor{N}}, args...; included::Vector{Int}=Int[], optimality=mcc, verbose::Bool=false, bagfeatures::Bool=false, kwargs...) where {M <: Union{SDM, Bagging}, N}
```

厳密なVIFケースのための変数選択のバージョンです。これにより、モデルが悪化する可能性があり、この理由からクロスバリデーションは行われません。

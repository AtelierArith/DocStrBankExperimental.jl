```
struct ExogenousInputs
    intervention::Dict{Symbol, Dict}
    temperature::Dict{Symbol, Float64}
    function ExogenousInputs(;
        intervention = Dict{Symbol, Dict}(),
        temperature = Dict{Symbol, Float64}())
        new(intervention,
        temperature)
    end
end
```

シミュレーションされたシステムへの摂動のためのデータには、(1) 生物学的制御介入と (2) 外部で定義された温度系列/ショックが含まれます。

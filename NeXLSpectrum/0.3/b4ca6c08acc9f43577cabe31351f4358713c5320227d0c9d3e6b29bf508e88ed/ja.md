```
sigma(spec::Spectrum, specs::AbstractArray{<:Spectrum}, chs::AbstractRange{<:Integer})::Vector{Float64}
```

`spec` スペクトルが `specs` の他のスペクトルの平均からどれだけ偏っているかをチャネルごとに計算します。結果はカウント統計のみから期待される標準偏差の観点で表現されます。`spec` がカウント統計のみで変動すると仮定すると、結果の値は平均 0.0 および標準偏差 1.0 になると期待されます。

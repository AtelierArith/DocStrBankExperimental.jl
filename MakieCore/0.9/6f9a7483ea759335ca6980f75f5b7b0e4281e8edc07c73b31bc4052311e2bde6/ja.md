```
Plot{PlotFunc}(args::Tuple, kw::Dict{Symbol, Any})
```

`PlotFunc`に対応するプロットを作成します。各レシピは`Plot{PlotFunc}`のエイリアスを定義します。例:

```julia
const Scatter = Plot{scatter} # scatterレシピで定義
Plot{scatter}((1:4,), Dict{Symbol, Any}(:color => :red)) isa Scatter
# 同じ:
Scatter((1:4,), Dict{Symbol, Any}(:color => :red))
```

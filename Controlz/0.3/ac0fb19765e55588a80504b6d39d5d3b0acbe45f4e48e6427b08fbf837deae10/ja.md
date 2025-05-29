```
viz_poles_and_zeros(g, savename=nothing, title::String="ポールとゼロ")
```

転送関数 `g` のゼロとポールを複素平面にプロットします。

さらなる修正のために `CairoMakie.jl` の `Figure` オブジェクトを返します。

```
nyquist_diagram(tf, nb_pts=500, ω_max=10.0, savename=nothing)
```

伝達関数 `tf` のナイキスト図をプロットして、その周波数応答を視覚化します。`s=-1` は赤い `+` としてプロットされます。`nb_pts` は解像度を変更します。`ω_max` は考慮される最大周波数を指定します。

さらなる修正のために `CairoMakie.jl` の `Figure` オブジェクトを返します。

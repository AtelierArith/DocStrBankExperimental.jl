```
plotProject!(proj::Project, plotOptions::Int = 0)
```

`plotOptions`で指定されたオブジェクトをプロットします。`plotOptions`は、`MODEL`、`GRID`、`MESH`、`REFINEMENTS`の選択肢から描画するものの合計によって構成されます。

例: モデルとグリッドをプロットするには、`plotOptions = MODEL + GRID`とします。メッシュだけをプロットするには、`plotOptions = MESH`とします。

すべてをプロットするには、`plotOptions = MODEL + GRID + MESH + REFINEMENTS`とします。

内容は次の順序で重ねられます: `GRID`、`MESH`、`MODEL`、`REFINEMENTS`

!!! note "Makie.jlが必要です"
    この関数を機能させるには、REPLでMakie.jlをロードする必要があります（例: `using GLMakie`を呼び出す）。


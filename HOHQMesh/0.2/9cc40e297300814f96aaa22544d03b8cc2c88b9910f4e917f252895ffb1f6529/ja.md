```
updatePlot!(proj::Project, plotOptions::Int)
```

新しい plotOptions = 組み合わせ (合計) の再プロット

```
GRID, MESH, MODEL, REFINEMENTS
```

例: `updatePlot!(p, MESH + MODEL)`

!!! note "Makie.jl が必要です"
    この関数を機能させるには、REPL で Makie.jl をロードする必要があります (例: `using GLMakie` を呼び出す)。


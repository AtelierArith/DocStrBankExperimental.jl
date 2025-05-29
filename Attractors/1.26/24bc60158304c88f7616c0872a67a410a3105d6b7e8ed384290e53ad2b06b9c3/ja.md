```
convergence_and_basins_of_attraction(mapper::AttractorMapper, grid)
```

[`basins_of_attraction`](@ref) の拡張です。`basins, attractors, convergence` を返します。`basins, attractors` は `basins_of_attraction` と同様で、`convergence` は `basins` と同じ形状の配列です。これは、各初期条件がそのアトラクターに収束するのにかかった時間を含みます。これは [`shaded_basins_heatmap`](@ref) に渡すのに便利です。

[`convergence_time`](@ref) も参照してください。

# キーワード引数

  * `show_progress = true`: 進行状況バーを表示します。

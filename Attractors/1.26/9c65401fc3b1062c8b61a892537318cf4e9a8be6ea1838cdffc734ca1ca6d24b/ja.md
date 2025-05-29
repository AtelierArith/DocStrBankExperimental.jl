```
shaded_basins_heatmap(grid, basins, attractors, iterations; kwargs...)
```

見つかった（2次元の）`basins`のアトラクションと対応する`attractors`のヒートマップをプロットします。`basins`と同じサイズの行列`iterations`を提供する必要があり、この行列の値に応じて色をシェードします。小さな値は明るい色に、大きな値は暗いトーンに対応します。これは、各初期条件が収束するまでにかかる反復回数を表すのに便利です。反復回数を保存するために[`convergence_time`](@ref)も参照してください。

## キーワード引数

  * `show_attractors = true`: プロットにアトラクタを表示します
  * `maxit = maximum(iterations)`: `iterations`の値を`maxit`にクリップします。非常に長い反復がある場合に便利で、範囲を特定の区間に制限します。
  * すべての[共通プロットキーワード](@ref common_plot_kwargs)。

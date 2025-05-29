```
plot_attractors(attractors::Dict{Int, StateSpaceSet}; kwargs...)
```

アトラクターを散布図としてプロットします。

## キーワード引数

  * すべての [共通プロットキーワード](@ref common_plot_kwargs)。特に重要なのは `access` キーワードです。
  * `sckwargs = (strokewidth = 0.5, strokecolor = :black,)`: アトラクターをプロットする `Makie.scatter` 関数に伝播される追加のキーワードです。

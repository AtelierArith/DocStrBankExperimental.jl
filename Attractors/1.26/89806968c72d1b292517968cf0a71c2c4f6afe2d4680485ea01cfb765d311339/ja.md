```
plot_continuation_curves(continuation_info [, prange]; kwargs...)
```

[`plot_basins_curves`](@ref)と同様ですが、継続を特徴づける任意の量を視覚化します。したがって、`continuation_info`は`fractions_cont`とまったく同じ形式です：各辞書がアトラクターIDを実数にマッピングする辞書のベクターです。`continuation_info`は[`plot_attractors_curves`](@ref)の`attractors_cont`に付随することを意図しています。

`attractors_cont`から`continuation_info`を生成するには、次のようにします：

```julia
continuation_info = map(attractors_cont) do attractors
    Dict(k => f(A) for (k, A) in attractors)
end
```

ここで、`f`は実数を返す関心のある関数です。

## キーワード引数

  * `series_kwargs`: 曲線をプロットするために`Makie.scatterlines!`に伝播される引数の名前付きタプル。
  * また、すべての[共通プロットキーワード](@ref common_plot_kwargs)。

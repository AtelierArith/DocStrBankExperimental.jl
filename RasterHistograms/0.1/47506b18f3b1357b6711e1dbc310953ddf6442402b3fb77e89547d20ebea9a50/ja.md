```
function convert_arguments(P::Type{<:AbstractPlot}, arh::AbstractRasterHistogram)
```

`AbstractRasterHistogram`をプロットできるようにするための変換メソッド。**注意** プロットの目的のために、ゼロに対応する値は`NaN`に置き換えられます。これは、2Dプロットで多くのゼロ値を避け、結果として分布が明確に見えないようにするためです（Makie.jlの`heatmap`では、`NaN`値は[プロットから除外されます](https://docs.makie.org/stable/examples/plotting_functions/heatmap/#three_vectors)）。

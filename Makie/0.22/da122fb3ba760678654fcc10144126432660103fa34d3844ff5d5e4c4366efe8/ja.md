```
Legend(
    fig_or_scene,
    contents::AbstractArray,
    labels::AbstractArray,
    title = nothing;
    kwargs...)
```

`contents` と `labels` から凡例を作成します。各ラベルは1つのコンテンツ要素に関連付けられています。コンテンツ要素は、`AbstractPlot`、`AbstractPlots` の配列、`LegendElement`、または `legendelements` メソッドが定義されている他の任意のオブジェクトである可能性があります。

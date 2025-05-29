```
Legend(
    fig_or_scene,
    contentgroups::AbstractVector{<:AbstractVector},
    labelgroups::AbstractVector{<:AbstractVector},
    titles::AbstractVector;
    kwargs...)
```

`contentgroups`、`labelgroups`、および `titles` からマルチグループ凡例を作成します。 `contentgroups` と `labelgroups` の各グループは、`titles` の1つのタイトルに関連付けられています（タイトルは `nothing` にすることで非表示にできます）。

各グループ内では、各コンテンツ要素は1つのラベルに関連付けられています。コンテンツ要素は、`AbstractPlot`、`AbstractPlots` の配列、`LegendElement`、または `legendelements` メソッドが定義されている他の任意のオブジェクトである可能性があります。

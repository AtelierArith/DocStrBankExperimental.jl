```
plot!(plot, item; ...)
plot!(plot, type; ...)
```

プロットに新しいアイテムを追加するか、指定されたタイプのアイテムを追加します。

タイプを渡す場合、許可されるキーワード引数には、そのタイプが受け入れるものが含まれます。`item`または`type`が何であるかに応じて、追加の引数が許可される場合があります。

構築されたアイテムが返されます。グリフの場合、対応する [`GlyphRenderer`](@ref) が代わりに返されます。

## グリフ

追加のキーワード引数：

  * [`GlyphRenderer`](@ref) が受け入れるすべてのもの。
  * `source`: `data_source` のエイリアス。[`DataSource`](@ref)、列の `Dict`、または `Tables.jl` スタイルのテーブルである可能性があります。
  * `color`: すべての `*_color` プロパティのエイリアス。
  * `alpha`: すべての `*_alpha` プロパティのエイリアス。
  * `palette`: グリフに `color_mapper` プロパティがある場合、このパレットを持つ [`LinearColorMapper`](@ref) に設定されます。
  * `legend_label`
  * `legend_field`
  * `legend_group`
  * `filters`: ソースデータに適用するフィルタのリスト。

## レンダラー

これには軸、グリッド、凡例、およびその他の注釈が含まれます。

追加のキーワード引数：

  * `location`: `"center"`（デフォルト）、`"left"`、`"right"`、`"below"` または `"above"` のいずれか。
  * `dimension`: 軸の場合、`location` または `dimension` のいずれかを指定する必要があり、もう一方は推測されます。

## ツール

追加のキーワード引数：

  * `activate`: true の場合、ツールバーの同種のアクティブなツールとして設定します。

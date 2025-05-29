```
sgplot(ds, plots;
                mapformats=true,
                nominal=nothing,
                xaxis=Axis(),
                x2axis=Axis(),
                yaxis=Axis(),
                y2axis=Axis(),
                legend=true,
                threads=automatic,
                opts...)
```

統計グラフィックスを生成します。`ds` 引数はデータセット（またはグループ化されたデータセット）を指し、`plots` は Bar、Pie などのマークのベクターです。

`opts...` は `sgplot` に渡すことができる追加のキーワード引数を指します。これらのキーワードは、`ds` がデータセットかグループ化されたデータセットかによって異なります。以下に各ケースの利用可能なキーワード引数を示します。

# 非グループ化データセット

# キーワード引数

## プロットの外観

  * `backcolor`: グラフ全体の背景色。デフォルト: `:white`
  * `clip`: プロット全体のクリップオプション。デフォルト: `true`
  * `font`: デフォルトフォント。デフォルト: `"sans-serif"`
  * `fontweight`: フォントの太さの値。デフォルト: `400`
  * `groupcolormodel`: 特定のプロットに `group` が使用されるときに使用されるカラーモデル。デフォルト: `:category`
  * `height`: プロットの高さ。デフォルト: `400`
  * `italic`: パッケージがイタリックフォントを使用するかどうかのデフォルト値。デフォルト: `false`
  * `wallcolor`: プロットエリアの背景色。デフォルト: `:transparent`
  * `width`: プロットの幅。デフォルト: `600`

# グループ化データセット

```
overview_table(table)
```

`table`の列の要約概要を提供する`Table`を作成し、データセットの直感的な理解を提供することを目的としています。

グラフをLaTeXでレンダリングするには、前文に`\usepackage{tikz}`を含める必要があります。

## キーワード引数

  * `max_categories = 10`: カテゴリ列の個別にリストされるカテゴリの数を制限し、残りはまとめられます。
  * `label_metadata_key = "label"`: 列ラベルメタデータを参照するためのキー。

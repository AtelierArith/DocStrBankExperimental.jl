```
bregions!(builder::SimplexGridBuilder,grid,regionlist;facetregions=nothing)
```

`grid`のすべての境界ファセットを、領域リストの領域番号とともにジオメトリ記述に追加します。オプションのパラメータ`facetregions`を使用すると、`regionlist`の番号を上書きすることができます。

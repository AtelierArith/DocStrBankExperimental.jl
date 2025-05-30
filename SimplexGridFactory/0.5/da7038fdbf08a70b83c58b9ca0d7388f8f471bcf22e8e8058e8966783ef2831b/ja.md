```
bregions!(builder::SimplexGridBuilder,grid, pairs...)
```

`grid` の境界ファセットを、`pairs` の最初の要素として示された領域番号と、`pairs` の2番目の要素として示された領域番号を使用して、ジオメトリ記述に追加します。

例:

```
bregions!(builder,grid, 1=>2, 3=>5)
```

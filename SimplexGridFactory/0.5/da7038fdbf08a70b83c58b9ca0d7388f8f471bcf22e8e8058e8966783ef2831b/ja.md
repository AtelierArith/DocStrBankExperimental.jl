```
bregions!(builder::SimplexGridBuilder,grid, pairs...)
```

`grid` の境界ファセットに、`pairs` の最初の要素として言及された領域番号と、`pairs` の2番目の要素として言及された領域番号をジオメトリ記述に追加します。

例:

```
bregions!(builder,grid, 1=>2, 3=>5)
```

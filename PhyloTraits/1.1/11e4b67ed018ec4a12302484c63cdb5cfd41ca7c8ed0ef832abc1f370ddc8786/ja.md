```
RateVariationAcrossSites(rvsymbol::Symbol, ncategories::Int=4)
```

サイト間のレート変動のデフォルトモデルで、シンボルによって指定されます：

  * `:noRV` レート変動なし
  * `:G` または `:Gamma` ガンマ分布のレート
  * `:I` または `:Inv` 2つのカテゴリ：不変と変動
  * `:GI` または `:GI` 両方。

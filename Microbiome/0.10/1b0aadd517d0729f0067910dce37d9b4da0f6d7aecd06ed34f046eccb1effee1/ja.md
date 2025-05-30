```
featuretotals(at::AbstractAbundanceTable)
```

`at`の各行（特徴）の合計を返します。戻り値はnfeatures x 1の`Matrix`であり、`Vector`ではありません。1Dの`Vector`が必要な場合は、`vec(featuretotals(at))`を使用してください。

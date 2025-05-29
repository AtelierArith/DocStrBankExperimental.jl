```
sampletotals(at::AbstractAbundanceTable)
```

`at`の各行（特徴）の合計を返します。返り値は1 x nsamplesの`Matrix`であり、`Vector`ではありません。1Dの`Vector`が必要な場合は、`vec(sampletotals(at))`を使用してください。

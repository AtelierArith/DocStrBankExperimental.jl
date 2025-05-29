```
SearchParams(;
    maxpopulation::Int = 32
    bsize::Int = 16
    mutbsize::Int = 8
    crossbsize::Int = 8
    maxiters::Int = 300
    verbose::Bool = true
)
```

検索パラメータの可変リストを作成し、`inspect_population`を介してオンラインで変更できます。

  * `maxpopulation`: 各イテレーションで保持される構成の最大数（最小エラーに基づく）
  * `bsize`: 突然変異および交差手続きに使用される最良アイテムの数
  * `mutbsize`: 突然変異手続きからのイテレーションごとの新しい構成の数
  * `crossbsize`: 交差手続きからのイテレーションごとの新しい構成の数
  * `maxiters`: 検索手続きの最大イテレーション
  * `verbose`: 検索イテレーションの冗長性を制御します

```
classification_scores(gold, predicted; labelnames=nothing)
```

与えられたゴールドスタンダードと予測に対して、いくつかのスコアを計算します。具体的には、グローバルおよびクラスごとの粒度での精度、再現率、F1スコアです。labelnamesが指定されている場合、それはラベル名の配列です。

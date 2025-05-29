```
coefnames(model::TableRegressionModel{<:BetaRegressionModel})
```

`@formula`を使用してテーブルにフィットした`BetaRegressionModel`の係数名を文字列のベクトルとして返します。精度項は配列の最後の要素として含まれ、その名前は`"(Precision)"`です。

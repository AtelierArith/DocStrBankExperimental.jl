```
predict(am::UnivariateARCHModel, what=:volatility, horizon=1; level=0.01)
```

`am`から`horizon`ステップ先の予測を形成します。`what`は予測されるオブジェクトを制御します。選択肢は`:volatility`（デフォルト）、`:variance`、`:return`、および`:VaR`です。VaRレベルはキーワード引数`level`で制御できます。

すべての予測ターゲット/ボラティリティ仕様がマルチステップ予測をサポートしているわけではありません。

```
financial_scores(fmp, symbol)
```

指定されたシンボルの一般的な財務スコアを返します。

# 引数

  * `fmp::FMP`: 財務モデリング準備インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Financial-Scores](https://site.financialmodelingprep.com/developer/docs/#Stock-Financial-scores)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の財務スコアを取得
data = financial_scores(fmp, "AAPL")
```

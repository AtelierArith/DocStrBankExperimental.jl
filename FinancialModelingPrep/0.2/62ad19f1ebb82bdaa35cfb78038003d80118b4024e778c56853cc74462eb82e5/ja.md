```
price_targets_consensus(fmp, symbol)
```

指定されたシンボルの価格目標コンセンサスを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Price-Target-Consensus](https://site.financialmodelingprep.com/developer/docs/#Price-Target-Consensus)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の価格目標コンセンサスを取得
data = price_target_consensus(fmp, "AAPL")
```

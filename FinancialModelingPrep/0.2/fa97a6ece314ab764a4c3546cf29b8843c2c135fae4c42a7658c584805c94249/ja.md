```
upgrades_and_downgrades_consensus(fmp, symbol)
```

指定されたシンボルのコンセンサスのアップグレードとダウングレードを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Upgrades-&-Downgrades-Consensus](https://site.financialmodelingprep.com/developer/docs/#Upgrades-&-Downgrades-Consensus)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL のアップグレードとダウングレードのコンセンサスを取得
data = upgrades_and_downgrades_consensus(fmp, AAPL)
```

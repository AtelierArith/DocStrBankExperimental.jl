```
upgrades_and_downgrades(fmp, symbol)
```

指定されたシンボルのアップグレードとダウングレードを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Upgrades-&-Downgrades](https://site.financialmodelingprep.com/developer/docs/#Upgrades-&-Downgrades)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL のアップグレードとダウングレードを取得
data = upgrades_and_downgrades(fmp, AAPL)
```

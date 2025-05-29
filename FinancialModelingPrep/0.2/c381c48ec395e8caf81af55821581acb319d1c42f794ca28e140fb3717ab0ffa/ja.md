```
otc_quote(fmp, symbol)
```

指定されたシンボルの価格見積もりを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[OTC-Quote](https://site.financialmodelingprep.com/developer/docs/#Company-Quote)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# GBTC の OTC 見積もりを取得
data = otc_quote(fmp, "GBTC")
```

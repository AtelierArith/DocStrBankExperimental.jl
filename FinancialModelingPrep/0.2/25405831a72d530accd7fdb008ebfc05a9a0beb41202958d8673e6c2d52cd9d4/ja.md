```
price_targets_by_company(fmp, company)
```

指定された会社からの価格目標を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * company::String: アナリスト会社名。

詳細については、[Price-Target-by-Analyst-Company](https://site.financialmodelingprep.com/developer/docs/#Price-Target-by-Analyst-Company)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# Barclaysからの価格目標を取得
data = price_targets_by_company(fmp, company = "Barclays")
```

```
financial_ratios(fmp, symbol, params...)
```

指定されたシンボルの一般的な財務比率を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Financial-Ratios](https://site.financialmodelingprep.com/developer/docs/#Company-Financial-Ratios)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 過去30四半期のAAPLの財務比率を取得
data = financial_ratios(fmp, "AAPL", period = "quarter", limit = 30)
```

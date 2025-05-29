```
survivorship_bias(fmp, symbol, date)
```

指定されたシンボルの生存バイアスのJSON辞書を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。
  * `date::String`: yyyy-mm-dd形式の日付文字列。

詳細については[Survivorship-Bias](https://site.financialmodelingprep.com/developer/docs/#Survivorship-Bias-Free-EOD)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# AAPLの2012年1月3日の生存バイアスを取得
data = survivorship_bias(fmp, "AAPL", date = "2012-01-03")
```

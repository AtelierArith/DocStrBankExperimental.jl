```
equity_offerings_search(fmp, name)
```

指定された名前の株式提供日を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `name::String`: 会社名。

詳細については、[Equity-Offerings-Fundraising-Company-Search](https://site.financialmodelingprep.com/developer/docs/#Equity-offerings-Fundraising-Company-Search)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# Marinalife の株式提供日を取得
data = equity_offerings_search(fmp, name = "Marinalife")
```

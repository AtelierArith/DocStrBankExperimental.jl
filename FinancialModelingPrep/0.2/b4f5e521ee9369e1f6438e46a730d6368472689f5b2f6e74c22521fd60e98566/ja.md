```
company_from_cusip(fmp, cusip)
```

指定されたcusipに一致するすべての企業を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * cusip::String: cusip。

詳細については、[Cusip-Mapper](https://site.financialmodelingprep.com/developer/docs/#Form-13F)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# cusipに一致するすべての企業を取得
data = company_from_cusip(fmp, cusip = "000360206")
```

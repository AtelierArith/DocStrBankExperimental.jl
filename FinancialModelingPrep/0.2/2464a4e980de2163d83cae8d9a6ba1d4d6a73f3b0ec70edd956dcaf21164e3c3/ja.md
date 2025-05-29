```
filing_dates(fmp, cik)
```

指定されたCIKに一致するすべてのフォーム13Fの提出日を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `cik::String`: CIK。

詳細については、[Form-13F-Filing-Dates](https://site.financialmodelingprep.com/developer/docs/#Form-13F)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# CIKに一致するすべてのフォーム13Fの提出日を取得
data = filing_dates(fmp, cik = "0001067983")
```

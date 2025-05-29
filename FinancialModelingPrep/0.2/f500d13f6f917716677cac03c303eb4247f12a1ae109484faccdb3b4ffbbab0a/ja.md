```
company_from_cik(fmp, cik)
```

指定されたCIKに一致するすべての会社名を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `cik::String`: CIK。

詳細については、[CIK-Mapper](https://site.financialmodelingprep.com/developer/docs/#Form-13F)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# CIKに一致する会社名を取得
data = company_from_cik(fmp, cik = "0001067983")
```

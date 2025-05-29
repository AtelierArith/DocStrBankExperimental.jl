```
equity_offerings(fmp, cik)
```

指定されたCIKのクラウドファンディングオファリングを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `cik::String`: CIK。

詳細については、[Equity-Offerings-Fundraising-by-CIK](https://site.financialmodelingprep.com/developer/docs/#Equity-offerings-Fundraising-by-CIK)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# Marinalifeの株式オファリングを取得
data = equity_offerings(fmp, cik = "0001870523")
```

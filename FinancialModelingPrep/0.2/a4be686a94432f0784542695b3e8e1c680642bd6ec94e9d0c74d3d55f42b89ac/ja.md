```
crowdfunding_offerings(fmp, cik)
```

指定されたCIKのクラウドファンディングオファリングを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `cik::String`: CIK。

詳細については、[Crowdfunding-Offerings-by-CIK](https://site.financialmodelingprep.com/developer/docs/#Crowdfunding-Offerings-by-CIK)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# OYO Fitnessのクラウドファンディングオファリングを取得
data = crowdfunding_offerings(fmp, cik = "0001916078")
```

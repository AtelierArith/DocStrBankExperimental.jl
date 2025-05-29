```
company_profile(fmp, symbol)
```

指定されたシンボルの会社プロフィールを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Company-Profile](https://site.financialmodelingprep.com/developer/docs/#Company-Profile)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# AAPLの会社プロフィールを取得
data = company_profile(fmp, "AAPL")
```

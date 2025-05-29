```
crowdfunding_offerings_search(fmp, name)
```

指定された名前のクラウドファンディングオファリングの日付を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `name::String`: 会社名。

詳細については、[Crowdfunding-Offerings-Company-Search](https://site.financialmodelingprep.com/developer/docs/#Crowdfunding-Offerings-Company-Search)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# Enotapのクラウドファンディングオファリングの日付を取得
data = crowdfunding_offerings_search(fmp, name = "Enotap")
```

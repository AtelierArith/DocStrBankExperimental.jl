```
company_rating(fmp, symbol)
```

指定されたシンボルの評価を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Company-Rating](https://site.financialmodelingprep.com/developer/docs/#Company-Rating)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の会社評価を取得
data = company_rating(fmp, "AAPL")
```

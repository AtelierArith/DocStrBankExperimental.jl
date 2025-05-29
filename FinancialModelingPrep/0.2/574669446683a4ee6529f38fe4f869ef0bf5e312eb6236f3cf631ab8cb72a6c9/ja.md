```
sp500_companies(fmp, historical = false)
```

すべてのS&P 500企業を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `historical::Bool`: 歴史的な企業または現在の企業を返します。

詳細については、[List-of-S&P-500-Companies](https://site.financialmodelingprep.com/developer/docs/#List-of-S&P-500-companies)を参照してください。 詳細については、[Historical-S&P-500-Companies](https://site.financialmodelingprep.com/developer/docs/#Historical-S&P-500)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# すべての歴史的S&P 500企業のリストを取得
data = sp500_companies(fmp, historical = true)
```

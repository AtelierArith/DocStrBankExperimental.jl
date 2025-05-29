```
nasdaq_companies(fmp, historical = false)
```

すべてのナスダック企業を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `historical::Bool`: 歴史的な企業または現在の企業を返します。

詳細については、[List-of-Nasdaq-100-Companies](https://site.financialmodelingprep.com/developer/docs/#List-of-Nasdaq-100-companies)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# すべての歴史的なナスダック 100 企業のリストを取得
data = nasdaq_companies(fmp, historical = true)
```

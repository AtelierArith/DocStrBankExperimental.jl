```
dowjones_companies(fmp, historical = false)
```

ダウ・ジョーンズのすべての企業を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `historical::Bool`: 歴史的な企業または現在の企業を返します。

詳細については、[List-of-Dow-Jones-Companies](https://site.financialmodelingprep.com/developer/docs/#List-of-Dow-Jones-companies)を参照してください。 詳細については、[Historical-Dow-Jones-Companies](https://site.financialmodelingprep.com/developer/docs/#Historical-Dow-Jones)を参照してください。

# 例

```julia
# FMP APIのインスタンスを作成
fmp = FMP()

# すべての歴史的なダウ・ジョーンズ企業のリストを取得
data = dowjones_companies(fmp, historical = true)
```
